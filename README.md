# calculator
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace calculator_form
{
    public partial class calculator : Form
    {
        double operand1, operand2, result;

        private void btnsubtract_Click(object sender, EventArgs e)
        {
            try {
                operand1 = Convert.ToDouble(txtoperand1.Text);
                operand2 = Convert.ToDouble(txtoperand2.Text);
                result = operand1 - operand2;
                txtresult.Text = result.ToString();
            }
            catch (SystemException)
            {
                txtresult.Text = "syntax error";
                
            }

        }

        private void btnmulti_Click(object sender, EventArgs e)
        {
            try {
                operand1 = Convert.ToDouble(txtoperand1.Text);
                operand2 = Convert.ToDouble(txtoperand2.Text);
                result = operand1 * operand2;
                txtresult.Text = result.ToString();
            }
            catch (SystemException)
            {
               txtresult.Text = "syntax error";
                
            }

        }

        private void btndivide_Click(object sender, EventArgs e)
        {
            if (Convert.ToDouble(txtoperand2.Text)!=0)
            {
                operand1 = Convert.ToDouble(txtoperand1.Text);
                operand2 = Convert.ToDouble(txtoperand2.Text);
                result = operand1 / operand2;
                txtresult.Text = result.ToString();
            }
            else
            {
                txtresult.Text = "syntax error";


            }
        }
        private void txtoperand1_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (char.IsDigit(e.KeyChar) == false && char.IsControl(e.KeyChar) == false && (e.KeyChar == '.' ? txtoperand1.Text.Contains('.')==true:true))
            e.Handled = true;
        }

        private void txtoperand2_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (char.IsDigit(e.KeyChar) == false && char.IsControl(e.KeyChar) == false && (e.KeyChar == '.' ? txtoperand2.Text.Contains('.') == true : true))
                e.Handled = true;

        }

        private void btnclear_Click(object sender, EventArgs e)
        {
            txtoperand1.Text = "";
            txtoperand2.Text = "";
            txtresult.Text = "";
        }

        private void btnback_Click(object sender, EventArgs e)
        {

        }

        private int calculate_Factorial(int num)
        {
            int answer = 1;
            for (int x = 1; x <= num; x = x + 1)
                answer = answer * x;
            return answer;
        }

        private void btnfact_Click(object sender, EventArgs e)
        {
            try
            {
                int fact, answer;
                fact = int.Parse(txtoperand1.Text);
                answer = calculate_Factorial(fact);
                txtresult.Text = answer.ToString();
                txtoperand1.IsAccessible = true;

            }
            catch(SystemException)
            {
                txtresult.Text = "please enter a value in operand1";

            }
        }

        private void btnsqrt_Click(object sender, EventArgs e)
        {
            txtoperand1.Text = Convert.ToString(Math.Sqrt(Convert.ToDouble(txtresult.Text)));
        }

    

        public calculator()
        {
            InitializeComponent();
        }
        
        private void btnadd_Click(object sender, EventArgs e)
        {
            try {
                operand1 = Convert.ToDouble(txtoperand1.Text);
                operand2 = Convert.ToDouble(txtoperand2.Text);
                result = operand1 + operand2;
                txtresult.Text = result.ToString();
            }
            catch(SystemException)
            {
              txtresult.Text = "syntax error";
                

            }

        }
    }
}
