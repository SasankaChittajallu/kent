# kent
package bowling;
public class Game {
	 
	  int rolls[] = new int[21];
	  int currentThrow = 0;
	  public static void main(String[] args) {
					int score;
					int throwCount;
					int finalScore;
					int[] input = {1,4,4,5,6,4,5,5,10,0,0,1,7,3,6,4,10,0,2,8,6};				    				
					Game gm=new Game();					
					for(throwCount=0;throwCount<=20;throwCount++)
						{
							score=input[throwCount];
						
							if(score<=10 && score>=0)
							gm.roll(score);
						
							else if(score==10)
								throwCount++;
					    }
					
				 finalScore=	gm.score(gm.rolls);
				
				 System.out.println("final score is "+finalScore);
				
			 	}
			 	
	public void roll(int pins) {
					   rolls[currentThrow] = pins;
					   currentThrow++;
		       }
				
	int score(int[] a){
		
		int currentScore=0;
		int i;
		for(i=0;i<=20;i++){			
			
			if((i>2)&&i!=20){
				
					if((a[i-1]+a[i-2]==10)&&(i%2==0)) {
						
						currentScore=currentScore+(2*a[i]);
					}
					else if((a[i-3]==10)&&(i%2==1)) {
						
						currentScore=currentScore+2*(a[i]);
					}
					else {
						
						currentScore=currentScore+a[i];
					}
					
					if(i>3&&(a[i-2]==10&&a[i-4]==10)) {
					
						currentScore=currentScore+a[i];
					}
					else if(i>3&&(a[i-3]==10&&a[i-5]==10)&&i%2==1){
						
						currentScore=currentScore+a[i];
					}
					}
			
			else if(i==2){
				
				if((a[i-1]+a[i-2]==10)){
					
					currentScore=currentScore+(2*a[i]);
				}
				else{
					
					currentScore=currentScore+a[i];
				}
			}
			
			else{
					currentScore=currentScore+a[i];
					}
		}
		return currentScore;
	}
}
