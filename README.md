# DataStruct-Week4
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
class SinhVien
{
    public string id;
    public string name;
    public float dtb;
}
/*Tao mang 100k phan tu de sort va dung timing de do thoi gian*/
class Program
{
    /*Tìm các chỉ số đầu tiên.*/
    static int SeqSearch(int[] arr, int value)
    {
        for (int i = 0; i <= arr.Length; i++)
        {
            if (arr[i] == value)
            {
                return i;
            }
            else
            {
                continue;
            }
        }
        return -1;
    }
    /*Seq reverse*/
    static int SeqRev(int[]arr, int value)
    {
        for (int i = arr.Length-1; i >=0; i--)
        {
            if (arr[i] == value)
            {
                return i;
            }
            else
            {
                continue;
            }
        }
        return -1;
    }
    /*Tim ra tat ca cac chi so*/
    static List<int> SeqAll(int[] arr, int value)
    {
        List<int> list = new List<int>(arr.Length);
        for (int i = 0; i<= arr.Length - 1; i++)
        {
            if (arr[i] == value)
            {
                list.Add(i);
            }
            else
            {
                continue;
            }
        }
        return list;
        
    }
    /*Bo sung kien thuc de quy*/
    static long tong(int n)
    {
        if (n == 1)
        {
            return 1;
        }
        else
        {
            return tong(n - 1) + n;
        }
    }
    static long fac(int n)
    {
        if (n == 1)
        {
            return 1;
        }
        else
        {
            return fac(n - 1) * n;
        }
    }
    static int RecuSearch(int[] arr, int from, int value)/*from: vi tri bat dau tim kiem*/
    {
        if (arr.Length == 0)
        {
            return -1;
        }
        else
        {
            if (arr[from] == value)
            {
                return from;
            }
            else
            {
                if (from == arr.Length - 1)
                {
                    goto Stop;
                }
                else
                {
                    return RecuSearch((int[])arr, from + 1, value);
                }
            }
        }
    Stop:;
        return -1;
    }


    static int SenSearch(int[] A, int value)/*khac phuc nhuoc diem khong ton tai phan tu trong mang tim kiem*/
    {
        int x = A[A.Length - 1];
        A[A.Length - 1] = value;
        int i = 0;
        while (A[i] != value)
        {
            i++;
        }
        if ((i < A.Length - 1) && (A[A.Length - 1] == value))
        {
            return i;
        }
        else
        {
            return -1;
        }
    }
    static int BinSearch(int[] A, int T)/*yeu cau mang dau vao phai duoc xap sep*/
    {
        int lower = 0, upper = A.Length - 1, mid;
        while (lower <= upper)
        {
            mid = (lower + upper) / 2;
            if (A[mid] > T)
            {
                upper = mid - 1;
            }
            else if (A[mid] < T)
            {
                lower = mid + 1;
            }
            else
            {
                return mid;
            }
        }
        return -1;
    }

    static void Main(string[] args)
    {
        int[] arr = { 1, 2, 3, 4, 5, 3 };
        int[] A = { 2, 3, 4, 5, 6 };
        Console.WriteLine("Su dung RecuSearch: ");
        Console.WriteLine(RecuSearch(arr, 0, 3));
        Console.WriteLine("Su dung SeqSearch: ");
        Console.WriteLine(SeqSearch(arr, 3));
        Console.WriteLine("Su dung SeqRev: ");
        Console.WriteLine(SeqRev(arr, 3));
        Console.WriteLine("Su dung SeqAll: ");
        List<int> list = SeqAll(arr, 3);
        if (list.Count() == 0)
        {
            Console.WriteLine("So can tim khong co trong chuoi");
        }
        else
        {
            foreach(int x in list)
            {
                Console.Write("{0} ", x);
            }
        }
        Console.WriteLine();
        Console.WriteLine("Su dung SenSearch: ");
        Console.WriteLine(SenSearch(arr, 7));/*7 khong ton tai nen se tra ve -1*/
        /*static int SenSearcH(int[] arr, int value{
        int x = A[A.Length -1];
        int i = 0;
        while(arr[i] != value)
        {
            i++;
        }
        if (i <A.length -1 && A[A.length - 1] == value)
        {
            return i;
        } 
        else
        {
            return -1;
        }
        }
         */
        Console.WriteLine("Su dung BinSearch: ");
        Console.WriteLine(BinSearch(arr, 3));
        Console.WriteLine("Su dung BinSearch1: ");
        Console.WriteLine(BinSearch1(arr, 3));
        Console.Read();
        SinhVien st = new SinhVien();
        st.id = "SV01"; st.name = "Nguyen A"; st.dtb = 5.6f;
        SinhVien st1 = new SinhVien();
        st1.id = "SV02"; st1.name = "Nguyen B"; st1.dtb = 9.8f;
        SinhVien st2 = new SinhVien();
        st2.id = "SV03"; st2.name = "Nguyen C"; st2.dtb = 10.0f;

    }
    public static int BinSearch1(int[] arr, int value)
    {
        int lower = 0, upper = arr.Length - 1, mid;
        while (lower <= upper)
        {
            mid = (lower + upper) / 2;

            if (value > arr[mid])
            {
                lower = mid + 1;
            }
            else if (value < arr[mid])
            {
                upper = mid - 1;
            }
            else 
            {
                return mid;
            }
        }
        return -1;
    }
}

