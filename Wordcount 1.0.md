package test;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.io.*;
public class test2 extends JFrame implements ActionListener{
	JButton jb1,jb2,jb3=null;
	JLabel jt1,jt2,jt3,jt4=null;
	JPanel jp1,jp2,jp3=null;
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		test2 test_1=new test2();
	}
//构造函数
    public test2() {
//配置界面
    	jp1=new JPanel();
    	jp1.setLayout(new GridLayout(1,3));
    	jp2=new JPanel();
    	jp2.setLayout(new GridLayout(1,2));
    	jp3=new JPanel();
    	jp3.setLayout(new GridLayout(3,1));
    	jb1=new JButton("打开");
    	jb2=new JButton("统计");
    	jb3=new JButton("拓展功能");
       	jp1.add(jb1);
       	jp1.add(jb2);
    	jp1.add(jb3);
    	jt1=new JLabel();
    	jt2=new JLabel("字符数：");
    	jt3=new JLabel("单词数：");
    	jt4=new JLabel("句子数：");
    	jp3.add(jt2);
    	jp3.add(jt3);
    	jp3.add(jt4);
    	jp2.add(jt1);
    	jp2.add(jp3);
    	this.setLayout(new GridLayout(2,1));
    	this.add(jp2);
    	this.add(jp1);
    	this.setTitle("统计");
    	this.setSize(400,200);
    	this.setVisible(true);
    	this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    	jb1.addActionListener(this);
    	jb1.setActionCommand("打开");
    	jb2.addActionListener(this);
    	jb2.setActionCommand("统计");
    	jb3.addActionListener(this);
    	jb3.setActionCommand("拓展功能");
    }
//按下按键后的反馈
	@Override
	public void actionPerformed(ActionEvent arg0) {
		// TODO Auto-generated method stub
		if(arg0.getActionCommand().equals("打开")) {
			
		}
        if(arg0.getActionCommand().equals("统计")) {
			
			}
        if(arg0.getActionCommand().equals("拓展功能")) {
        	
	}

 }
}