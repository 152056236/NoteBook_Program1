# NoteBook_Program1
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;


namespace CSharpNoteBook
{
    class Program
    {
        static void Main(string[] args)
        {
            //string URL = @"D:\C#\新建文件夹\";
            Text text=new Text();
            TextFile textfile=new TextFile();
            bool a = true;
            bool b=true;
            while (a)
            {
                try
                {
                    Console.WriteLine("*********************************************");
                    Console.WriteLine("*                                           *");
                    Console.WriteLine("*        1:新建/删除笔记  2:打开笔记        *");
                    Console.WriteLine("*        3:输入/保存笔记  4:新建文件夹      *");
                    Console.WriteLine("*        5:管理文件夹     6:退出            *");
                    Console.WriteLine("*                                           *");
                    Console.WriteLine("*********************************************");
                    Console.Write("请输入菜单选项（1-6）");
                    int choice = Int32.Parse(Console.ReadLine());                    
                    switch (choice)
                    {
                        case 1:
                          b = true;
                            while (b)
                            {
                                Console.Clear();
                                Console.WriteLine("************************************************************");
                                Console.WriteLine("*                     新建笔记菜单                         *");
                                Console.WriteLine("*        1:新建笔记                    2:删除笔记          *");
                                Console.WriteLine("*        3:退出本菜单                                      *");
                                Console.WriteLine("************************************************************");
                                Console.Write("请输入菜单选项(1-3):");
                                choice = Int32.Parse(Console.ReadLine());
                                    switch (choice)
                                    {
                                case 1:
                                    text.Add();
                                    Console.ReadKey();
                                    break;
                                case 2:
                                    text.Delete();
                                    Console.ReadKey();
                                    break;
                                case 3:
                                    b = false;
                                    break;
                                default:
                                    Console.WriteLine("请输入1-3！");
                                    Console.ReadLine();
                                    break;
                                   }
                          }
                                    break;
                        case 2:
                                 b = true;
                            while (b)
                            {
                                Console.Clear();
                                Console.WriteLine("************************************************************");
                                Console.WriteLine("*                     打开笔记菜单                         *");
                                Console.WriteLine("*        1:打开笔记                    2:退出本菜单        *");
                                Console.WriteLine("************************************************************");
                                Console.Write("请输入菜单选项(1-2)");
                                choice = int.Parse(Console.ReadLine());
                                switch (choice)
                                {
                                    case 1:
                                        text.Read();
                                        Console.ReadKey();
                                        break;
                                    case 2:
                                        b = false; 
                                        break;
                                    default:
                                        Console.WriteLine("输入错误！！请输入数字(1-2)！按任意键继续。");
                                        Console.ReadKey();
                                        break;
                                }
                            }

                            break;
                        case 3:
                              b = true;
                            while (b)
                            {
                                Console.Clear();
                                Console.WriteLine("************************************************************");
                                Console.WriteLine("*                   输入/保存笔记笔记菜单                  *");
                                Console.WriteLine("*        1:输入/保存笔记             2:退出本菜单          *");
                                Console.WriteLine("*                                                          *");
                                Console.WriteLine("************************************************************");
                                Console.Write("请输入菜单选项(1-2):");
                                choice = int.Parse(Console.ReadLine());
                                switch (choice)
                                {
                                    case 1:
                                        text.Write();
                                        Console.ReadKey();
                                        break;
                                    case 2:
                                        b = false;
                                        break;
                                    default:
                                        Console.WriteLine("输入错误！！请输入数字(1-2)！按任意键继续。");
                                        Console.ReadKey();
                                        break;
                                }
                            }
                            break;
                        case 4:
                             b = true;
                            while (b)
                            {
                                Console.Clear();
                                Console.WriteLine("************************************************************");
                                Console.WriteLine("*                     新建文件夹菜单                       *");
                                Console.WriteLine("*        1:新建文件夹                    2:退出本菜单      *");
                                Console.WriteLine("************************************************************");
                                Console.Write("请输入菜单选项(1-2):");
                                choice= int.Parse(Console.ReadLine());
                                switch (choice)
                                {
                                    case 1:
                                        textfile.Add();
                                        Console.ReadKey();
                                        break;
                                    case 2:
                                        b = false; 
                                        break;
                                    default:
                                        Console.WriteLine("输入错误！！请输入数字(1-2)！按任意键继续。");
                                        Console.ReadKey();
                                        break;
                                }
                            }
                            break;
                        case 5:
                             b = true;
                            while (b)
                            {
                                Console.Clear();
                                Console.WriteLine("************************************************************");
                                Console.WriteLine("*                     管理文件夹菜单                       *");
                                Console.WriteLine("*        1:删除文件夹                    2:查看文件夹      *");
                                Console.WriteLine("*        3:退出本菜单                                      *");
                                Console.WriteLine("************************************************************");
                                Console.Write("请输入菜单选项(1-3):");
                                choice = int.Parse(Console.ReadLine());
                                switch (choice)
                                {
                                    case 1:
                                        Console.WriteLine("有以下文件夹：");
                                        foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\"))
                                        {
                                            Console.WriteLine(" "+d);
                                        }
                                        textfile.Delete();
                                        Console.ReadKey();
                                        break;
                                    case 2:
                                        textfile.Read();
                                        Console.ReadKey();
                                        break;
                                    case 3: b = false; break;
                                    default:
                                        Console.WriteLine("输入错误！！请输入数字(1-2)！按任意键继续。");
                                        Console.ReadKey();
                                        break;
                                }
                            }
                            break;
                        case 6:
                            a = false;
                            break;
                        default:
                            Console.Write("请输入1-6");
                            Console.ReadKey();
                            break;
                    }
                }
                catch
                {
                    Console.WriteLine("输入错误！！！！！");
                }
            }
        }
    }
        }
 using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace CSharpNoteBook
{
    abstract class Message
    {
            //文件名
            private string _TextName;
            protected string TextName
            {
                get { return _TextName; }
                set { _TextName = value; }
            }
            //文件夹名
            private string _TextFileName;
            protected string TextFileName
            {
                get { return _TextFileName; }
                set { _TextFileName = value; }
            }
            public abstract void Add(); //添加
            public abstract void Delete();//删除
            public abstract void Write();//输入
            public abstract void Read();//输出
        }
    
}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;

namespace CSharpNoteBook
{
    class Text:Message
    {
        public override void Add()
        {
            Console.WriteLine("请选择要把新建笔记放入以下哪个文件夹中：");
            foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\"))
            {
                Console.WriteLine(" " + d);
            }
            TextFileName = Console.ReadLine();
            if (TextFileName.Length != 0)
            {
                if (Directory.Exists(@"D:\C#\新建文件夹\" + TextFileName))
                {
                    Console.WriteLine("请输入要创建文件的名字：");
                    TextName = Console.ReadLine();
                    if (TextName.Length != 0)
                    {
                        if (!File.Exists(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt"))
                        {
                            FileStream fs1 = File.Create(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt");
                            Console.WriteLine("成功,文件名叫：{0}", TextName + ".txt");
                            fs1.Close();
                        }
                        else
                            Console.WriteLine("失败,已存在文件名为：{0}的文件！", TextName + ".txt");
                    }
                    else
                        Console.WriteLine("笔记名字不能为空！！");
                }
                else
                    Console.WriteLine("失败！没有该文件：{0}", TextFileName);
            }
            else
                Console.WriteLine("文件夹名字不能为空！！");
        }

        public override void Delete()
        {
            Console.WriteLine("请选择要删除哪个文件夹下的笔记：");
            foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\"))
            {
                Console.WriteLine(" " + d);
            }
            TextFileName = Console.ReadLine();
            if (TextFileName.Length != 0)
            {
                if (Directory.Exists(@"D:\C#\新建文件夹\" + TextFileName))
                {
                    Console.WriteLine("有以下文件：");
                    foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\" + TextFileName + "\\"))
                    {
                        Console.WriteLine(" " + d);
                    }
                    Console.WriteLine("请输入要删除文件的名字：");
                    TextName = Console.ReadLine();
                    if (TextName.Length != 0)
                    {
                        if (File.Exists(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt"))
                        {
                            File.Delete(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt");
                            Console.WriteLine("成功，删除的文件名叫：{0}", TextName + ".txt");
                        }
                        else
                            Console.WriteLine("失败,{0}的文件不存在！", TextName + ".txt");
                    }
                    else
                        Console.WriteLine("笔记名字不能为空！！");
                }
                else
                    Console.WriteLine("失败！没有该文件：{0}", TextFileName);
            }
            else
                Console.WriteLine("文件夹名字不能为空！！");
        }

        public override void Read()
        {
            Console.WriteLine("请选择要打开以下哪个文件夹中的笔记：");
            foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\"))
            {
                Console.WriteLine(" " + d);
            }
            TextFileName = Console.ReadLine();
            if (TextFileName.Length != 0)
            {
                if (Directory.Exists(@"D:\C#\新建文件夹\" + TextFileName))
                {
                    Console.WriteLine("有以下文件：");
                    foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\" + TextFileName + "\\"))
                    {
                        Console.WriteLine(" " + d);
                    }
                    Console.WriteLine("请输入要操作的文件名：");
                    TextName = Console.ReadLine();
                    if (TextName.Length != 0)
                    {
                        if (File.Exists(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt"))
                        {
                            Console.WriteLine(System.IO.File.ReadAllText(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt", Encoding.Default));
                            Console.WriteLine("成功！");
                        }
                        else
                            Console.WriteLine("错误！{0}文件不存在", TextName + ".txt");
                    }
                    else
                        Console.WriteLine("笔记名字不能为空！！");
                }
                else
                    Console.WriteLine("失败！没有该文件：{0}", TextFileName);
            }
            else
                Console.WriteLine("文件夹名字不能为空！！");
        }

        public override void Write()
        {
            Console.WriteLine("请选择要在哪个文件夹下输入笔记：：");
            foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\"))
            {
                Console.WriteLine(" " + d);
            }
            TextFileName = Console.ReadLine();
            if (TextFileName.Length != 0)
            {
                if (Directory.Exists(@"D:\C#\新建文件夹\" + TextFileName))
                {
                    Console.WriteLine("有以下文件：");
                    foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\" + TextFileName + "\\"))
                    {
                        Console.WriteLine(" " + d);
                    }
                    string ss;
                    Console.WriteLine("请输入要操作的文件名：");
                    TextName = Console.ReadLine();
                    if (TextName.Length != 0)
                    {
                        if (File.Exists(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt"))
                        {
                            Console.WriteLine("请输入需要输入的信息：");
                            ss = Console.ReadLine();
                            File.AppendAllText(@"D:\C#\新建文件夹\" + TextFileName + "\\" + TextName + ".txt", ss, Encoding.Default);//可在文本后面加字符串
                            Console.WriteLine("成功！");
                        }
                        else
                            Console.WriteLine("{0}文件不存在，请新建！", TextName + ".txt");
                    }
                    else
                        Console.WriteLine("笔记名字不能为空！！");
                }
                else
                    Console.WriteLine("失败！没有该文件：{0}", TextFileName);
            }
            else
                Console.WriteLine("文件夹名字不能为空！！");
        }
    }
    }

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;

namespace CSharpNoteBook
{
    class TextFile:Message
    {
         public override void Add()
        {
            Console.WriteLine("请输入要创建文件夹的名字：");
            TextFileName = Console.ReadLine();
            if (TextFileName.Length != 0)
            {
                if (Directory.Exists(@"D:\C#\新建文件夹\" + TextFileName) == false)
                {
                    Directory.CreateDirectory(@"D:\C#\新建文件夹\" + TextFileName); //如果文件夹不存在，直接创建文件夹。
                    Console.WriteLine("成功");
                }
                else
                    if (Directory.Exists(@"D:\C#\新建文件夹\" + TextFileName))
                    {
                        Console.WriteLine("{0}：文件夹已有！！", @"D:\C#\新建文件夹\" + TextFileName);
                    }
            }
            else
                Console.WriteLine("文件夹名字不能为空！！");
        }
        public override void Delete()
        {
            Console.WriteLine("请输入要删除的文件夹名字：");
            TextFileName = Console.ReadLine();
            if (TextFileName.Length != 0)
            {
                if (Directory.Exists(@"D:\C#\新建文件夹\" + TextFileName)) //如果存在这个文件夹删除之 
                {
                    Directory.Delete(@"D:\C#\新建文件夹\" + TextFileName);
                    Console.WriteLine("成功！");
                }
                else
                    Console.WriteLine("{0}此文件夹不存在！", @"D:\C#\新建文件夹\" + TextFileName);
            }
            else
                Console.WriteLine("文件夹名字不能为空！！");
        }
        public override void Write()
        {
            throw new NotImplementedException();
        }
        public override void Read()
        {
            Console.WriteLine("已创建的文件夹如下：");
            foreach (string d in Directory.GetFileSystemEntries(@"D:\C#\新建文件夹\"))
            {
                Console.WriteLine(" " + d);
            } }  }
    }

