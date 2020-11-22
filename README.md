# shiyan5
shiyan5
一、 实验目的
1. 掌握字符串String及其方法的使用
2. 掌握文件的读取/写入方法
3. 掌握异常处理结构
二、 文件处理部分要求
在某课上,学生要提交实验结果，该结果存储在一个文本文件A中。
文件A包括两部分内容：
1. 学生的基本信息；
2. 学生处理后的作业信息，该作业的业务逻辑内容是：利用已学的字符串处理知识编程完成《长恨歌》古诗的整理对齐工作，写出功能方法，实现如下功能：
1) 每7个汉字加入一个标点符号，奇数时加“，”，偶数时加“。”
2) 允许提供输入参数，统计古诗中某个字或词出现的次数
3) 输入的文本来源于文本文件B读取，把处理好的结果写入到文本文件A
4) 考虑操作中可能出现的异常，在程序中设计异常处理程序

三、 学生类部分要求：
1. 设计学生类（可利用之前的）；
2. 采用交互式方式实例化某学生；
3. 设计程序完成上述的业务逻辑处理，并且把“古诗处理后的输出”结果存储到学生基本信息所在的文本文件A中。
四、 实验流程
1. 建立学生类，要求如下：
1) 设立带有修饰符private的字符串型变量name，number，team
2) 创建变量对应的set与get函数，用来赋值与获取
3) 利用toString来复写学生类，方便后面的写入文件
五、 核心代码
以下代码展示了Java如何读取文件，如何处理文件中的字符串，利用字节流来读取文件，以及用字符流来将字节转换为字符，并将字符流存储在字符型数组中，并结合数组下标来将处理好的字符赋值在动态字符串中。
public static StringBuffer ReadTxt(String path) {
        StringBuffer s = new StringBuffer();
        // 读取文件内容 (输入流)
        try {
            FileInputStream out = new FileInputStream(path);
            InputStreamReader isr = new InputStreamReader(out);
            char[] chars = new char[9999999];
            int ch = 0;
            int i = 0;
            while ((ch = isr.read()) != -1) {
                chars[i] = (char) ch;
                i++;
            }
            for (int j = 0; j < i; j++) {
                s.append(chars[j]);
                if ((j + 1) % 7 == 0 && (j + 1) % 2 == 0) {
                    s.append("。" + "\n");
                }
                if ((j + 1) % 7 == 0 && (j + 1) % 2 != 0) {
                    s.append("，");
                }
            }
        } catch (Exception e) {
            System.out.println("1");
        }
        return s;
    }
六、 实验结果



