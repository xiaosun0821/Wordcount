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
	    String path=null;
	    char zifu[]=null;
	    char paths[]=null;
	//按下按键后的反馈
	//@Override
		public void actionPerformed(ActionEvent arg0) {
			// TODO Auto-generated method stub
			if(arg0.getActionCommand().equals("打开")) {
				this.open();
			}
	        if(arg0.getActionCommand().equals("统计")) {
				this.tongji();
				}
	        if(arg0.getActionCommand().equals("拓展功能")) {
	        	this.tuozhan();
		}
	
	 }
	//打开函数
			public void open(){
				JFileChooser jfc=new JFileChooser();
				jfc.setDialogTitle("请选择文件。。。");
				jfc.showOpenDialog(null);
				jfc.setAcceptAllFileFilterUsed(false);
				jfc.setVisible(true);
			    path=jfc.getSelectedFile().getAbsolutePath();
			    paths=path.toCharArray();
			    jt1.setText(path);
	 }
	//统计函数
			public void tongji() {
				if(path!=null&&paths[paths.length-1]=='t'
					    &&paths[paths.length-2]=='x'&&paths[paths.length-3]=='t'
					    &&paths[paths.length-4]=='.')
		           {
					int l=0;
					int len=0;
				    StringBuffer str=new StringBuffer("");
				    File file=new File(path);
				    try {
				        FileInputStream is=new FileInputStream(file);
				        InputStreamReader isr= new InputStreamReader(is);
				        BufferedReader in= new BufferedReader(isr);
				        String line=null;
				        while( (line=in.readLine())!=null )
				        {   
				        	if(line.trim().length()==0) {
				        		l++;
				        	}	
				        	if(len != 0) 
	// 处理换行符的问题
				            {
				                str.append("\r\n"+line);
				            }
				            else
				            {
				                str.append(line);
				            }
				            len++;
				        }
				        in.close();
				        isr.close();
				        is.close();
				    } catch (IOException e) {
	// TODO Auto-generated catch block
				        e.printStackTrace();
				    }
				    String s=str.toString();
				    zifu=s.toCharArray();
				    int zfs=0;//字符数
					int dcs=0;//单词数
					int jzs=0;//句子数
					if(zifu[0]!=' '){
						dcs++;
					}
				for(int i=0;i<zifu.length;i++) {
					if(zifu[i]!=' '&&zifu[i]!='\n'&&zifu[i]!='\r') {
						zfs++;
						}
					if(zifu[i]==' '&&i!=zifu.length-1&&zifu[i+1]!=' ') {
						dcs++;
					}
			
					if(zifu[i]=='\n') {
						dcs++;
					}
					if(zifu[i]=='.'||zifu[i]=='!'||zifu[i]==';'||zifu[i]=='?') {
						jzs++;
						}
					}
				jt2.setText("字符数："+zfs);
				jt3.setText("单词数："+(dcs-l));
				jt4.setText("句子数"+jzs);
			}
			}