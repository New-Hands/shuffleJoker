# shuffleJoker
my first project
package shuffle;

public class pPoker {//洗牌人
	private poker []poker=new poker[54];
	private String []point;
	private String[] color;
	public pPoker()
	{
		
		point=new String [] {"A","2","3","4","5","6","7","8","9","10","j","Q","k"};
		 color=new String []{ "♥", "♣", "♦", "♠"};
		 int k=0;
		 for(int i=0;i<13;i++)
		 {
			 for(int j=0;j<4;j++)
			   {poker[k]=new poker(point[i],color[j]);k++;}
		 }
			poker[52]=new poker("JOKER","小");
			poker[53]=new poker("JOKER","大");
	}
	public poker[] getPokerPoint()
	{
		for(int i=0;i<54;i++)
		{
			System.out.print(poker[i].color+poker[i].point);
		}
		return poker.clone();
	}
	public void shuffleOne()
	{
		String []temC=new String[54];
		String []temP=new String[54];
		for(int j=0;j<3;j++)
		{
		for(int i=0;i<54;i++)
		{
			 temC[i]=poker[i].color;
			 temP[i]=poker[i].point;
		}
	
		for(int i=0;i<27;i++)
		{
			 poker[2*i].color=temC[i+27];
			 poker[2*i].point=temP[i+27];
			 poker[2*i+1].color=temC[i];
			 poker[2*i+1].point=temP[i];
		}
		}
	}
	public void shuffleTwo()
	{
		for(int i=0;i<53;i++)
		{
			int t=(int)(Math.random()*(53-i));
			poker tem=poker[t]; 
			poker[t]=poker[53-i];
			poker[53-i]=tem;
		}
		
	}
	public void shufffeThree()
	{
		
		for(int i=0;i<54;i++)
		{
			int r=(int)(Math.random()*54);
			if(poker[i]!=poker[r])
			{
				poker temp=poker[i];
				poker[i]=poker[r];
				poker[r]=temp;
			}
		}
	}
}
//******************************
package shuffle;

public class poker {//牌
	 
	 	public String point;
	 	public String color;
	 	public poker(String x,String y)
	 	{
	 		point=x;
	 		color=y;
	 	}
	 
}
//***************
package shuffle;
public class shuffle {//提供了三种洗牌的算法

	public static void main(String[] args) {
	pPoker a=new pPoker();//洗牌人a
	System.out.println("请验牌***************");	
	a.getPokerPoint();
	System.out.println();
	System.out.println("洗牌。。。");
	a.shuffleOne();
	a.getPokerPoint();
	System.out.println();
	System.out.println("洗牌。。。");
	pPoker b=new pPoker();
	b.shuffleTwo();//洗牌人b
	b.getPokerPoint();
	System.out.println();
	System.out.println("洗牌。。。");
	pPoker c=new pPoker();//洗牌人c
	c.shufffeThree();
	c.getPokerPoint();
	}
}

