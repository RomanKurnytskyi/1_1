using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DelegatEx1
{
    class Program
    {

        delegate double Operation(double a,double x,double b);
        static double Func(double x)
        {
            return 2*x+Math.Log(x);
        }

        static double Max(double a,double x,double b)
        {
            double max;
            max = Func(b);
            if (max < Func(x))
                max = Func(x);
            return max;
        }
        static double Min(double a,double x, double b)
        {
            double min;
            min = Func(a);
            if (min > Func(x))
                min = Func(x);
            return min;
        }
        jfejffkhjjsdfjkfkjefksdflffvf



        static void Main(string[] args)
        {
            double a, b, h;
            Console.Write("Enter a:");
            a = Convert.ToDouble(Console.ReadLine());
            Console.Write("Enter b:");
            b = Convert.ToDouble(Console.ReadLine());
            Console.Write("Enter the function's step:");
            h = Convert.ToDouble(Console.ReadLine());

            Operation del = new Operation(Max);
            Operation del1 = new Operation(Min);
            if (a > b)
                Console.Write("Error occured.Enter the correct numbers");
            else
            {
                double x = a;
                double max=0;
                double min=0;
                for(double i=a;i<=b;i=i+h)
                {
                    Console.WriteLine("F(x)={0}",Func(x));

                    max=del.Invoke(a, x, b);
                    min=del1.Invoke(a, x, b);
                    x += h;

                }
                Console.WriteLine(max);
                Console.WriteLine(min);
                Console.ReadKey();
            }

        }
    }
}
