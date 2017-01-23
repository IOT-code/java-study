# java-study
I am learning Java, these small programs are my little practice
这是运行在Eclipse上的  万年历程序
package 类的部分总结;
import java.text.DateFormat;                           //这是一些列方法所需要的包
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;
import java.util.Calendar;
import java.util.GregorianCalendar;
import java.util.Scanner;
public class vc {

	public static void main(String[] args) {               							//main主函数入口
		System.out.println("请输入日期：（格式2030-5-1）"); 
		Scanner scanner=new Scanner(System.in);
		String temp=scanner.nextLine();

		System.out.println(temp);//
		                        //提醒客户需要输入的日期
		//String temp="2017-4-21";                                                     //简易模式是 提前输入日期，以字符串方式输入
		System.out.println("你输入的日期是"+temp);                                    //
		DateFormat format=new SimpleDateFormat("yyyy-MM-dd");                    //格式化字符串，按照预定的格式
		
		try {                                                                   
			Date date=format.parse(temp);										//把字符串‘temp代表的字符串’ 转换为日期
			Calendar calendar=new GregorianCalendar();
			calendar.setTime(date);                                                //以calendar方式存下日期
			int f=calendar.get(Calendar.DATE);                             //记下客户选择日期的具体几号，方便下面标记醒目日期
			//System.out.println(f);
			calendar.set(Calendar.DATE, 1);          //，周三，获得这一天是这周周几，初始化为一号，因为都是从一号开始进行排序的
			
			 calendar.get(Calendar.DAY_OF_WEEK);//一号周几                              判断出每月一号是一周的周几，因为从周几开始进行排序
			 //System.out.println("这是一周的周几"+calendar.get(Calendar.DAY_OF_WEEK));
			 int maxDate=  calendar.getActualMaximum(Calendar.DATE);//判断这个月有几天，这是总共循环的次数
			 
			System.out.println("日\t一\t二\t三\t四\t五\t六");                      //打印表格
		for(int i=0;i<calendar.get(Calendar.DAY_OF_WEEK)-1;i++)     //进行一个月第一天之前的空格打印
		    {                                
				System.out.print('\t');//表格格式化
			}
		     int j=calendar.get(Calendar.DAY_OF_WEEK)-1;
			//int j=Calendar.DAY_OF_WEEK-1;                        //记下这一天是周几，由于周日是一号，因此算出来的号数减去1就是具体的周几
			
			for(int i=1;i<=maxDate;i++)                            //总共天数次遍历进行打印
				
			{
		        if(i==f) System.out.print("*");             		//if(i!=f) System.out.print(i+"\t");               // 判断是否是用户指定的那一天，如果是就用星号进行标记
				System.out.print(i+"\t");//else System.out.print(i+"*\t");
				j++;
				if(j%7==0){
					System.out.println('\n');
				          }
			}
		} catch (ParseException e) {
			// TODO 自动生成的 catch 块
			e.printStackTrace();
		}
		//scanner=NULL;
	}
}
