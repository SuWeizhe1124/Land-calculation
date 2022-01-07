# Land-calculation

#--完成日期 (1-7)- 土地計算 避免手算耗時 處理大量數據-#

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class land {
	static float INT;
	public static void main(String[] args) throws IOException {
		//---------------土地謄本---------------------//
	      float num1, num2, num3,num4,num5,num6,num7,num8,num9,num10,num11;
	       	Scanner scanner = new Scanner(System.in);
	        System.out.print("土地地號 : ");
	        num1 = scanner.nextFloat();
	   //------------土地標示部-----------------------//
	        System.out.print("土地面積 : ");
	        num2 = scanner.nextFloat();
	        System.out.print("土地公告地質價元 :");
	        num3 = scanner.nextFloat();
	        System.out.println("土地面積坪數：" + num2*0.3025 +  " 總公告地質價元 : "+num2* num3 );
	        System.out.println("1坪的價元 : "+num3/0.3025+"總平方坪數價元 : "+num3/0.3025*num2*0.3025);
	       //---------------土地所有權部--------------//
	        System.out.print("登記次序 : 屬於一胎填1 屬於二胎填2 \n");
	        num4 = scanner.nextInt();
	        if(num4==1)
	        {
	        	  System.out.print("屬於一胎 ");
	        }
	        if(num4==2)
	        {
	        	  System.out.print("屬於二胎 ");
	        }
	        if(num4!=1&&num4!=2)
	        {
	        	System.out.print("輸入錯誤  \n\n\n\n\n\n");
	        }
	        //--------------------------------------------//
	        System.out.print("登記原因: 買賣輸入1  繼承2 \n");
	        num10 = scanner.nextFloat();
	        if(num10==1)
	       {
	        	  System.out.print("登記原因: 買賣\n");
	       }
	       if(num10==2)
	       {
	    		  System.out.print("登記原因: 繼承\n");
	       }
	       //----------------------------------------------//
	       System.out.print("土地他向權力部");   
	      //------------------土地他項--------------------//
	       System.out.print("\n 他有幾項需要登記");
	       num11 = scanner.nextFloat();
	       System.out.print("\n他有"+num11+"項");
	       float[][] num =     go1(num11,num2);
	   /*     System.out.print("\n 擔保債眷總金額:");
	        num5 = scanner.nextFloat();
	        System.out.print("輸入權力種類 最高額抵押 為0 普通為1 : ");
	        num6 = scanner.nextFloat();
	        if(num6==0)
	        {
	        	  System.out.print("屬於最高 "+num5/1.2);
	        }
	        if(num6==1)
	        {
	        	  System.out.print("屬於普通 ");
	        }
	        //--------------------------------------------------//
	       System.out.print("\n債眷額比例幾分:");
	       num7=scanner.nextFloat();
	       System.out.print("\n債眷額比例之幾:");
	       num8=scanner.nextFloat();
	       System.out.print("\n歷年取德的範圍:"+(num2*num8/num7*0.3025));	  
	       //----------------------------------------------------------//
	       */
	       //------------------------------------------------------------//
	       File writename = new File("C:\\Users\\zxc78\\Desktop\\土地公告地質\\地號名稱"+num1+".txt"); // 相對路徑，如果沒有則要建立一個新的output。txt檔案
	       writename.createNewFile(); // 建立新檔案
	       BufferedWriter out = new BufferedWriter(new FileWriter(writename));
	       out.write("土地公告值檔案\r\n"); // \r\n即為換行
	       out.write("土地地號 :"+num1+"\r\n");
	       out.write("土地面積 :"+num2+"\r\n");
	       out.write("土地面積坪數：" + num2*0.3025 +  " 總公告地質價元 : "+num2* num3 +"\r\n");
	       out.write("1坪的價元 : "+num3/0.3025+"總平方坪數價元 : "+num3/0.3025*num2*0.3025+"\r\n");
	       //---------------------------------------------------------------//
	       if(num4==1)
	        {
	    	   out.write("屬於一胎\r\n ");
	        }
	        if(num4==2)
	        {
	        	out.write("屬於二胎\r\n  ");
	        }
	        //------------------土地他項--------------------//
	        if(num10==1)
		       {
	        	out.write("登記原因: 買賣\r\n");
		       }
		       if(num10==2)
		       {
		    	   out.write("登記原因: 繼承\r\n");
		       }
	        //----------------注意這裡要看他的登記次序有多少-----------------//
	       for(int i=0;i<num.length;i++)
	       {
	    	   out.write("\n 第:"+(i+1)+"項擔保債眷總金額:");
	    	   out.write("\n 擔保債眷總金額: "+ num[i][0]);
	    	   if(num[i][1]==1)
		        {
		    	   out.write("屬於最高額抵押 "+num[i][0]/1.2+"\r\n");
		        }
		        if(num[i][1]==0)
		        {
		        	 out.write("屬於普通\r\n");
		        }
		       out.write(" "+num11+"\r\n");
		       out.write("債眷額比例幾分:"+  num[i][2]+"\r\n");
		       out.write("債眷額比例之幾:"+num[i][3]+"\r\n");
		       out.write("歷年取德的範圍:"+num[i][4]+"\r\n");
	       }
	       out.flush(); // 把快取區內容壓入檔案
	       out.close(); // 最後記得關閉檔案
	       System.out.print("確定OK_紀錄");
	       //---------------------------------------------------------------//
	}
	public static float[][] go1 (float num11,float num2) 
	{
		Scanner scanner = new Scanner(System.in);
		float[][] num = new float[(int) num11][5];
		for(int i=0;i<num.length;i++)
		{
			 System.out.print("\n 第:"+(i+1)+"項擔保債眷總金額:");
			 num[i][0] = (float) scanner.nextFloat();
		     System.out.print("輸入權力種類 最高額抵押 為1 普通為0 : ");
		     num[i][1] = (int) scanner.nextFloat();
		     if( num[i][1]==1)
		        {
		        	  System.out.print("屬於最高 "+ num[i][0]/1.2);
		        }
		        if( num[i][1]==0)
		        {
		        	  System.out.print("屬於普通 ");
		        }
		        System.out.print("\n債眷額比例幾分:");
		        num[i][2]=(float) scanner.nextFloat();
		        System.out.print("\n債眷額比例之幾:");
		        num[i][3]=(float) scanner.nextFloat();
		        System.out.print("\n歷年取德的範圍:"+(num2* num[i][2]/num[i][3]*0.3025));	
		        num[i][4]= (float) (num2* num[i][2]/num[i][3]*0.3025);
		}
		  System.out.print("測試用 - OK 沒問題");
       return  num;
	}
}
