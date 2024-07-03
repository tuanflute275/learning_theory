## Lý Thuyết C#


    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace LearnCsharp
    {
        internal class Program
        {
            static void Main(string[] args)
            {
                /* 
                 //hello world 
                 Console.WriteLine("hello world");

                        // vẽ hình trái tim 
            Console.WriteLine("******************************");
            Console.WriteLine("***    0 0 0 0   0 0 0 0    ***");
            Console.WriteLine("***  0 0 0 0 0 0 0 0 0 0 0  ***");
            Console.WriteLine("***  0 0 0 0 0 0 0 0 0 0 0  ***");
            Console.WriteLine("***    0 0 0 0 0 0 0 0 0   ***");
            Console.WriteLine("***      0 0 0 0 0 0 0     ***");
            Console.WriteLine("***        0 0 0 0 0       ***");
            Console.WriteLine("***          0 0 0         ***");
            Console.WriteLine("***            0           ***");
            Console.WriteLine("******************************");


                        // khai báo biến ==> type name = value
            string name = "nguyen van a";
            int age = 19;
            Console.WriteLine("xin chao toi ten la " + name);
            Console.WriteLine("tôi nam nay da " + age + " tuoi roi !!");

            int a = 20;
            int b = 30;
            int sum = a + b;    
            float div = (float)a / b;
            Console.WriteLine("ket qua phep cong la:" + sum);
            Console.WriteLine("ket qua phep chia la:" + div);

                        // các phép toán số học
            //toán tử toán học: + - * / % ++ --
            float a = (float)100.25; // có hai cách ép kiểu như vậy
            float b = 127.28f;
            string msg = "phep tong hai so la: ";
            Console.WriteLine("đay la so a: "+ a);
            Console.WriteLine("đay la so b: " + b);
            Console.WriteLine(msg + (a + b));

                        //toán tử gán: = += -= *= /= &= |= ^= >>= <<= 
            int c = default;
            int a = 120; 
            int b = a;
            c = b;
            bool bo = default;
            string str = default;
            Console.WriteLine(bo);
            Console.WriteLine("c= "+c);

                        //toán tử so sánh: == != > < >= <=
            int a = 125, b = 250;
            bool isCheck = a > b;
            Console.WriteLine(isCheck);
            Console.WriteLine(a == b);
            Console.WriteLine(a != b);

                        //toán tử logic: ! && ||
            int a = 120, b = 333, c = 343;
            bool isOk = (a % 2 == 0) || (b % 2 == 0);
            Console.WriteLine(isOk);
            bool isOk1 = (a % 2 == 0) && (b % 2 == 0);
            Console.WriteLine(isOk1);
            bool isCood = (c % 2 == 0);
            Console.WriteLine(!isCood);

                        //Nhập dữ liệu vào từ bàn phím
            Console.WriteLine("nhap ho va ten: ");
            string fullName = Console.ReadLine();

            Console.WriteLine("nhap tuoi cua ban: ");
            //int convert
            int age = Convert.ToInt32(Console.ReadLine()); //cach 1
            //int age = System.Int32.Parse(Console.ReadLine()); // cach 2

            //float convert
            Console.WriteLine("nhap diem trung binh cua ban: ");
            float avg = Convert.ToSingle(Console.ReadLine());
            Console.WriteLine("hello " + fullName + '\n' + "nam nay ban da: " + age + " tuoi" + '\n' + "toi da dat dc diem trung binh la: " + avg);


                        //Cách chạy file C# đơn lẻ trong Visual Studio
            // nếu có nhiều file thì file nào cũng có chứa void main vậy nên khi chạy sẽ lỗi
            //fix => nhấn chuột phải vào file k muốn chạy chọn property chọn Compile -> none
            // chỉ giữ lại file cần chạy là ok
            // tạo file mới chuột phải vào project -> add > new item > đặt tên > ok
            // tạo project mới -> chuột phải vào so

            // Các cách hiển thị dữ liệu ra màn hình
            int a = Convert.ToInt32(Console.ReadLine());
            int b = Convert.ToInt32(Console.ReadLine());
            int sum = a + b;

            //cách 1
            Console.WriteLine("c1: sum = " + sum);

            //cách 2
            Console.WriteLine("c2: sum = {0} + {1} = {2}", a, b, sum);

            //cách 3
            Console.WriteLine($"c3: sum = {a} + {b} = {sum}");

                        // Math
            //max
            int max = Math.Max(10, 55);
            //min
            float min = Math.Min(-12.4f, 55);
            // abs --> trị tuyệt đối
            double d = Math.Abs(-5);
            // sqrt --> căn bậc 2
            double t = Math.Sqrt(9);

            //
            Console.WriteLine("max = " + max);
            // chi tiết hon
            Console.WriteLine($"Max({10}, {43}) = {max} ");
            Console.WriteLine($"Min({-12.4f}, {55}) = {min} ");
            Console.WriteLine("abs = " + d);
            Console.WriteLine("sqrt = " + t);
            Console.WriteLine("Pi = " + Math.PI);\

                        //  Chú thích trong chương trình
            // 
            // chú thích nhiều dòng -> bôi đen -> ctrl k ctrl c 
            // bỏ chú thích nhiều dòng --> bôi đen -->  ctrl k ctrl u

                        // làm việc với chuỗi 
            string fullName = "tuan flutef    ";
            string msg = "275";
            string fullName2 = fullName.Trim();
            Console.WriteLine("do dai chuoi la k co trim() = " + fullName.Length);
            Console.WriteLine("do dai chuoi la trim() = " + fullName2.Length);
            Console.WriteLine("xoa khoan trang hai dau va viet thuong " + fullName.Trim().ToLower());
            Console.WriteLine("xoa khoan trang hai dau va viet hoa " + fullName.Trim().ToUpper());
            Console.WriteLine(fullName.Contains("f")); // tìm kiếm chữ t trong chuỗi nếu có trả về true k thì false
            Console.WriteLine(fullName.IndexOf("f")); // tìm kiếm vi trí chữ t trong chuỗi nếu có trả về đúng vị trị đó đang đứng
            Console.WriteLine(fullName.LastIndexOf("f")); // tìm kiếm vi trí chữ t trong chuỗi nếu có trả về đúng vị trị đó đang đứng nhưng lastIndex sẽ tìm từ phải sang

                        // Cấu trúc rẽ nhánh if else
            Console.WriteLine("nhap vao mot so bat ki: ");
            float a = Convert.ToSingle(Console.ReadLine());
            if (a % 2 == 0)
            {
                Console.WriteLine("đay la so chan");
            }
            else if (a % 3 == 0)
            {
                Console.WriteLine("day la so le");
            }
            else
            {
                Console.WriteLine("khong hop le!!");
            }


                        // Cấu trúc switch case
            Console.WriteLine("nhap vao mot ngay trong tuan: ");
            int day = Convert.ToInt32(Console.ReadLine());
            switch(day)
            {
                case 1:
                    Console.WriteLine("monday");
                    break;
                case 2:
                    Console.WriteLine("tuesday");
                    break;
                case 3:
                    Console.WriteLine("wednesday");
                    break;
                case 4:
                    Console.WriteLine("thurday");
                    break;
                case 5:
                    Console.WriteLine("friday");
                    break;
                case 6:
                    Console.WriteLine("saturday");
                    break;
                case 7:
                    Console.WriteLine("sunday");
                    break;
                default:
                    Console.WriteLine("vui long nhap dung ngay trong tuan (1-7)");
                    break;
            }

                        // Toán tử ba ngôi
            // variable = (condition) ? expressionTrue : expressionFalse;
            int a = 18;
            string msg = default;
            msg =  (a >= 18)  ? "ban da du 18 tuoi" : "ban chua du 18 tuoi";
            Console.WriteLine(msg);


                        // Vòng lặp for
            //for (khoi_tao; dieu_kien; buoc_nhay)
            //{
            //    // noi dung lăp
            //}

            Console.WriteLine("nhap vao so lan lap: ");
            int n = Convert.ToInt32(Console.ReadLine());
            for (int i = 0; i <= n; i++)
            {
                if (i % 2 == 1)
                {
                    continue;
                }
                Console.WriteLine("kq = " + i);
            }


                        // Vòng lặp while - khi không biết trước số lần lặp - điều kiện sai là ngừng chạy
            //while (dk)
            //{
            // noi dung lap
            //}
            int n = Convert.ToInt32(Console.ReadLine());
            int i = 0;
            while(i < n)
            {
                if(i % 2 != 0)
                {
                    Console.WriteLine(i);
                }
                i++;
            }


                        //  Vòng lặp do-while -- vẫn chạy ít nhất 1 lần dù dk sai
            int x = 120;
            do
            {
                Console.WriteLine(x);
                x++;
            } while (x < 100);



                        // Vòng lặp lồng nhau
            for(int i = 1; i <= 10; i++)
            {
                for(int j = 0; j <= 10; j++)
                {
                    Console.WriteLine($"{i} x {j} = {i*j}");
                }
                Console.WriteLine();
            }


            // break và continue
            // break - ngắt câu lệnh chủ yếu dùng trong switch case 
            // continue - bỏ qua và cho đi tiếp kết hợp với if else // ví dụ nếu là số lẻ thì continue và hiện ra số chẵn


            //Khai báo, khởi tạo, cấp phát mảng 
            // type[] name ;
            //string[] cars = new string[10];
            //int[] numbers = new int[20];
            string[] friends = new string[] { "lan", "hung", "yen", "toan", "ha" };

            // lấy phần tử trong mảng
            Console.WriteLine(friends[friends.Length - 1]);

            // for i
            Console.WriteLine("=============== FOR VOI I =============");
            for (int i = 0; i < friends.Length; i++)
            {
                Console.WriteLine(friends[i]);
            }

            Console.WriteLine("=============== SU DUNG FOREACH =============");
            foreach (var friend in friends)
            {
                Console.WriteLine(friend);
            }

            Console.WriteLine("=============== SAU SAP XEP =============");
            Array.Sort(friends);
            foreach (var friend in friends)
            {
                Console.WriteLine(friend);
            }
            //Sử dụng chức năng của lớp Array
            int[] numbers = { 1, 2, 8, 8, 4, 7, 3, 6, 8, 9, 3, 7, 9, 0 };

            //Array.Sort(numbers); // tang dan cac gia tri trong mang
            //Array.Reverse(numbers); // giam dan cac gia tri trong mang
            //Array.Clear(numbers, 0, numbers.Length); // set tat ca cac gia tri ve mac dinh
            int indexOfName = Array.IndexOf(friends, "yen"); // tìm vị trí của mang

            Console.WriteLine("sap xep mang voi array");
            foreach (var item in numbers)
            {
                Console.WriteLine(item);
            }

            Console.WriteLine("vi tri trong mang la: " + indexOfName);



            // Mảng hai chiều
            // mang vuong
            int[,] matrix = new int[10, 10];
            bool[,] cons = new bool[5, 7];
            string[,] msg = new string[5, 5];

            int row = cons.GetLength(0); // so hang
            int col = cons.GetLength(1); // so cot

            //Console.WriteLine($"so hang: {row}, so cot: {col}"); // hiển thị

            //ví dụ 2
            for (int i = 0;i < matrix.GetLength(0); i++)
            {
                for (int j = 0;j < matrix.GetLength(1); j++)
                {
                    Console.WriteLine(matrix[i, j] + " ");
                }
                Console.WriteLine();
            }

            //mang ziczac
            int[][] matrix2 = new int[10][];    
            for (int i = 0; i < matrix2.Length; i++)
            {
                matrix2[i] = new int[1 + i];
            }
            row = matrix2.Length;
            int colOfRow = matrix2[8].Length; // so cot cua hang thu 1
            Console.WriteLine($"so hang: {row}, so cot: {colOfRow}");

            // ví dụ 2
            for (int i = 0; i < matrix2.Length; i++)
            {
                for (int j = 0; j < matrix2[i].Length; j++)
                {
                    Console.WriteLine(matrix2[i][j] + " ");
                }
                Console.WriteLine();
            }

                        // SU DUNG PHUONG THUC
            int sum = Sum(20, 45);
            ShowResult(sum);

            // VIẾT Ở NGOÀI STATIC NÀY
                    static int Sum(int a, int b)
        {
            int sum = a + b;
            return sum;
        }
        static double div(int a = 0, int b = 0)
        {
            return 1.0 * a/b;
        }
        static void ShowResult(int n)
        {
            Console.WriteLine(n);
        }


                        // Tham số mặc định của phương thức
            ShowInfo("tuba", 18);
            ShowInfo();

            // viết ở ngoài static này
                    static void ShowInfo(string name = "" , int age = 0)
        {
            Console.WriteLine($"name = {name}");
            Console.WriteLine($"age = {age}");
        }


        ===================== out modifier


             static void main(string[] args)
        {
            // out modifier

            GetUSerInfo(out string name, out int age, out string address); // alt + enter -> tao nhanh phuong thuc
            // out để public cái dữ liệu mà mình gọi phuong thức truyền vào,
            // nếu k có từ khóa out trc các tham so thì khi gọi và truyen vao gia tri no se khong nhan du lieu
            // và khi đã sdung từ khóa out thì bắt buôc phải gán giá trị cho chúng nếu k sẽ lỗi
            // su dung từ khóa out rồi thì k cần gán giá trị ban đầu nữa
            ShowResult(name, age, address);
        }

        private static void ShowResult(string name, int age, string address)
        {
            Console.WriteLine("name = " + name);
            Console.WriteLine("age = " + age);
            Console.WriteLine("address = " + address);
        }

        private static void GetUSerInfo(out string name, out int age, out string address)
        {
            Console.WriteLine("nhap ten");
            name = Console.ReadLine();

            Console.WriteLine("nhap tuoi");
            age = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("nhap dia chi");
            address = Console.ReadLine();
        }



            =====================  ref modifier

             static void Main()
        {
            // ref
            // gần giống out nhưng mềm dẻo hơn khi sdung ref thì tham so có the khai bao hoạc không
            // nhưng bắt buộc phải khởi tạo giá trị ban đầu
            // như trv hợp dưới đây thì mark dc gắn default là 7 và k có từ khóa ref vậy nên kẻ cả khi nhập thì nó cũng k thay đổi

            // giống nhau giữa out và ref là đều cho phép thay đổi giá trị của đối số
            // dvs out thì nó k cần khai báo và khởi tạo giá trị ban đầu mà khai báo ngay khi sử dung từ out trong phương thức --> out string name
            // và khi su dung thì bắt buộc phải gán giá trị trong phương thức cho nó
            // dvs ref thì mềm dẻo hơn k cần phải gán giá trị trong phuong thức nhưng bắt buộc phải khai báo và khởi tạo giá trị ban đầu

            string name="";
            int age= default;
            float mark = 7.0f;
            GetUSerInfo(ref name , ref age, mark);
            ShowResult(name, age, mark);
        }
        private static void ShowResult(string name, int age, float mark)
        {
            Console.WriteLine("name = " + name);
            Console.WriteLine("age = " + age);
            Console.WriteLine("mark = " + mark);
        }

        private static void GetUSerInfo(ref string name, ref int age,  float mark)
        {
            Console.WriteLine("nhap ten");
            name = Console.ReadLine();

            Console.WriteLine("nhap tuoi");
            age = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("nhap diem");
            mark = Convert.ToSingle(Console.ReadLine());
        }


         static void main()
        {
            float[] marks = { 1, 20.3f, 5, 6, 7.5f, 8, 9 };
            int math = 9;
            float bio = 8.5f;
            // float avg = Avg(math, bio, 6, 8.5f, 9); // lỗi khi không có params
            // params nó giúp ta có thể truyền vào nhiều đối số 
            float avg = Avg(math, bio, 6, 8.5f, 9);
            Console.WriteLine($"Diem trung binh la: {avg}");
        }


         static float Avg(params float[] marks)
        {
            float sum = 0;
            foreach (var mark in marks)
            {
                sum += mark;
            }
            return (marks.Length == 0) ? 0 : sum / marks.Length;
        }

        =========================== các biến thể của Main()

                //static void Main()
        //{

        //}
        //static void Main(string[] args)
        //{
        //    Console.WriteLine("hello");
        //}
        //static int Main(string[] args)
        //{
        //    return 0;
        //}
        static int Main(string[] args)
        {

            return 0; //thành công --> trả về 1 số int
            // return ra các giá trị khác 0 , là kết quả trả về cuối cùng  nhưng có lỗi
            // string[] args là nhận vào các tham số mặc định
        }

        ==================================================
        // var ten_bien = gia_tri;
        var a = 10;
        --> nó sẽ tự suy luận ra kiểu của biến a là int luôn
        ==> gia trị phải là 1 giá trị cụ thể nếu k nó k suy luận ra kiểu dc --> k thể là null 
        ==> đã suy luận là int rồi thì sẽ k gán dc kiểu khác






            */

            // code




        }
        // static code



    }
}

## tobe continue