## 공학용 계산기 만들기 (C# 윈도우 폼)

윈도우즈 프로그래밍의 과제로 공학용 계산기를 만드는게 나왔다.

윈도우10의 계산기를 켜본적이 없어 몰랐는데 , 일반 계산기와 공학용 계산기의 사칙연산의 차이점이 있었다.

3+2*3 을 하면 일반 계산기의 답은 15가 나왔고, 공학용 계산기의 답은 9이다.

아마 대다수의 사람들이 초등학교에서 배운 사칙연산의 계산 방식을 통해 9라는 답을 내놨을 것이다.

곱셈 나눗셈을 먼저 계산 한후 덧셈 뺄셈을  하는 것이 보통 사람들이 아는 계산 방법이다.



그럼 본론으로 들어와서 과제를 수행하기 위해 내가 생각해서 처리해야하는 부분은 총 두가지이다. 

첫번째는 곱셈 나눗셈 과 덧셈 뺄셈의 우선 순위를 정해 준다음에 계산 할때 우선순위가 높은 것을 먼저 계산 하는것인데, 여기서 보통의 해결방법은 스택을 이용한 방법이다. 



이 과제에서 첫번째 처리해야 할 부분인 곱셈과 나눗셈의 우선순위 해결방법은 * 또는 / 이 나오면 계산을 미리미리 해서 스택에 넣는 방법이다.

```c#
if (stackOper.Count > 0)    //  stack.Peek이 비어있을때 호출 시 오류 방지
{
   if (stackOper.Peek() == '/' || stackOper.Peek() == '*' || stackOper.Peek() == '%')
      {
         switch (stackOper.Pop())    // 우선순위를 해결하기 위해 * 또는 / 는 미리 계산 후 스택에 삽입
         {
       case '*': stackNum.Push(stackNum.Pop() * Convert.ToDouble(buff)); buff = ""; break;
       case '/':
            if (Convert.ToDouble(buff) == 0) { textBox1.Text = "0으로 나눌수 없음"; return; }
       stackNum.Push(stackNum.Pop() / Convert.ToDouble(buff)); buff = ""; break;
       case '%': stackNum.Push(stackNum.Pop() % Convert.ToDouble(buff)); buff = ""; break;
         }
       }
 }
              
```



내가 두번째로 처리해야 할 부분은 소수점 처리인데 소수점은 세번째 자리까지 표현하였고, 올림, 반올림, 버림중 선택을 해야하는데 쉽게 가기위해 버림을 했다.  Math 메소드를 이용해도 되지만 , 일단 내가 아는 기술내에 해결하기 위해 ToString으로 했다.

```c#
double result;
string a = result.ToString("N3");		// 소수점 3자리 까지 표현
result = Convert.ToDouble(a);
```



![윈프 계산기](./img/계산기.png)



메인소스

```c#
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace _201101561계산기
{
    public partial class 은찬_계산기 : Form
    {
        string buff = "";         // 임시 보관 할 변수
        string output = "";      // 임시 출력 할 변수
        char oper;               // 연산자 저장할 변수 + , - , * , /
        double result;          // 결과 값 저장할 변수 
        int checkNum = 0;       // 연속 계산을 위한 체크 변수

        Stack<double> stackNum = new Stack<double>();
        Stack<char> stackOper = new Stack<char>();

        public 은찬_계산기()
        {
            InitializeComponent();
        }

        private void bt_num_click(object sender, MouseEventArgs e)
        {
            Button btn = (Button)sender;
            // 숫자 키 중 어느 것이 눌러졌는지를 저장
            buff += btn.Text;      //  3      // 3이 아니고 15면 두번 호출
            output += btn.Text;   // 3   ,   
            textBox1.Text = output;  // 3
            if (stackOper.Count > 0)        //  stack.Peek이 비어있을때 호출 시 오류 방지
            {
                if (stackOper.Peek() == '/' || stackOper.Peek() == '*' || stackOper.Peek() == '%')
                {
                    switch (stackOper.Pop())    // 우선순위를 해결하기 위해 * 또는 / 는 미리 계산 후 스택에 삽입
                    {
                        case '*': stackNum.Push(stackNum.Pop() * Convert.ToDouble(buff)); buff = ""; break;
                        case '/':
                            if (Convert.ToDouble(buff) == 0) { textBox1.Text = "0으로 나눌수 없음"; return; }
                            stackNum.Push(stackNum.Pop() / Convert.ToDouble(buff)); buff = ""; break;
                        case '%': stackNum.Push(stackNum.Pop() % Convert.ToDouble(buff)); buff = ""; break;
                    }
                }
            }
        }

        private void bt_oper_click(object sender, MouseEventArgs e)
        {
            Button btn = (Button)sender;
            if (buff != "")stackNum.Push(Convert.ToSingle(buff));
            buff = "";    // 0
            output += btn.Text;   // 3  + 
            textBox1.Text = output; // 3 + 15
            oper = btn.Text[0];   // +  
            checkNum++;
            stackOper.Push(btn.Text[0]);
        }

        private void bt_clear_click(object sender, MouseEventArgs e)
        {
            textBox1.Text = "";
            buff = "";
            output = "";
            result = 0.0;
        }

        private void bt_calc_click(object sender, MouseEventArgs e)
        {
            Button btn = (Button)sender;
            if (buff != "") stackNum.Push(Convert.ToDouble(buff));
            buff = "";

            while (stackOper.Count > 0)
            {
                switch (stackOper.Pop())
                {
                    case '+': stackNum.Push(stackNum.Pop() + stackNum.Pop()); break;
                    case '-': stackNum.Push(stackNum.Pop() - stackNum.Pop()); break;
                    case '^':
                        double temp1 = stackNum.Pop();
                        double temp2 = stackNum.Pop();
                        stackNum.Push(Math.Pow(temp2, temp1)); break;
                    case '!':
                        float facto = 1;
                        for(int i = (int)stackNum.Pop(); i > 0; i--)
                            facto *= i;
                        stackNum.Push(facto);
                        break;
                    case '√':
                        double root = Math.Sqrt(stackNum.Pop());
                        string a = root.ToString("N3");     // 소수점 3자리 까지 표현
                        stackNum.Push(Convert.ToDouble(a));
                    break;
                }
            }
            result = stackNum.Pop();
            string b = result.ToString("N3");
            result = Convert.ToDouble(b);
            output += btn.Text + result.ToString();
            buff = Convert.ToString(result);
            textBox1.Text = output;
            
        }
    

        private void Form1_Load(object sender, EventArgs e)
        {
            textBox1.Text = output;
        }

        private void bt_Exit(object sender, MouseEventArgs e)
        {
            Application.Exit();
        }
    }
}

```

