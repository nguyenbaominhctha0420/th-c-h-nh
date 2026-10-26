using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApplication5
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            using System;

namespace QuanLySinhVien_De1
    {
        // Câu 1: Xây dựng lớp Person
        class Person
        {
            // Thuộc tính
            public string HoTen { get; set; }
            public int NamSinh { get; set; }

            // Hàm tạo không tham số
            public Person()
            {
                HoTen = "";
                NamSinh = 2000;
            }

            // Hàm tạo có tham số
            public Person(string hoTen, int namSinh)
            {
                HoTen = hoTen;
                NamSinh = namSinh;
            }

            // Phương thức nhập thông tin
            public virtual void NhapThongTin()
            {
                Console.Write("Nhập họ tên: ");
                HoTen = Console.ReadLine();
                Console.Write("Nhập năm sinh: ");
                NamSinh = int.Parse(Console.ReadLine());
            }

            // Phương thức xuất thông tin
            public virtual void XuatThongTin()
            {
                Console.WriteLine($"Họ tên: {HoTen} | Năm sinh: {NamSinh}");
            }
        }

        // Câu 2: Xây dựng lớp SinhVien kế thừa từ Person
        class SinhVien : Person
        {
            // Bổ sung thuộc tính
            public string MaSV { get; set; }
            public double DiemTrungBinh { get; set; }

            // Hàm tạo không tham số
            public SinhVien() : base()
            {
                MaSV = "";
                DiemTrungBinh = 0.0;
            }

            // Hàm tạo có tham số sử dụng base
            public SinhVien(string hoTen, int namSinh, string maSV, double diemTrungBinh) : base(hoTen, namSinh)
            {
                MaSV = maSV;
                DiemTrungBinh = diemTrungBinh;
            }

            // Viết phương thức XepLoai() theo điểm trung bình
            public string XepLoai()
            {
                if (DiemTrungBinh >= 8.0)
                    return "Giỏi";
                else if (DiemTrungBinh >= 6.5)
                    return "Khá";
                else if (DiemTrungBinh >= 5.0)
                    return "Trung bình";
                else
                    return "Yếu";
            }

            // Câu 3: Nhập thông tin sinh viên
            public override void NhapThongTin()
            {
                Console.Write("Nhập mã sinh viên: ");
                MaSV = Console.ReadLine();
                base.NhapThongTin(); // Gọi phương thức nhập của lớp cha (Họ tên, Năm sinh)
                Console.Write("Nhập điểm trung bình: ");
                DiemTrungBinh = double.Parse(Console.ReadLine());
            }

            // Câu 3: Xuất thông tin sinh viên kèm xếp loại
            public override void XuatThongTin()
            {
                Console.WriteLine($"\n--- THÔNG TIN SINH VIÊN ---");
                Console.WriteLine($"Mã SV: {MaSV}");
                Console.WriteLine($"Họ tên: {HoTen}");
                Console.WriteLine($"Năm sinh: {NamSinh}");
                Console.WriteLine($"Điểm trung bình: {DiemTrungBinh}");
                Console.WriteLine($"Xếp loại: {XepLoai()}");
            }
        // Câu 4: Chương trình chính
        class Program
        {
            static void Main(string[] args)
            {
                // Thiết lập hiển thị tiếng Việt có dấu trên Console
                Console.OutputEncoding = System.Text.Encoding.UTF8;

                // Tạo đối tượng SinhVien
                SinhVien sv = new SinhVien();

                // Gọi phương thức nhập thông tin
                Console.WriteLine("=== NHẬP THÔNG TIN ===");
                sv.NhapThongTin();

                // Gọi phương thức xuất thông tin
                sv.XuatThongTin();

                Console.ReadKey();
            }
        }
         }
