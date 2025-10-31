# Java_Concurrency_introduction
Simple program - introduction to. Java concurrency



import java.util.concurrent.TimeUnit;

public class Main {
    public static void main(String[] args) {

      //  Thread customThread = Thread.currentThread();

        CustomThread customThread = new CustomThread();
        customThread.start();

        Runnable myRunnable = ()->{
            for(int i = 1; i <= 8; i++){
                System.out.print(" 2 ");
                try{
                    TimeUnit.SECONDS.sleep(1);
                }
                catch (InterruptedException e){
                    e.printStackTrace();
                }
            }
        };

        Thread myThread = new Thread(myRunnable);
        myThread.start();

        for(int i = 1; i <=3; i++){
            System.out.print(" 3 ");
            try{
                Thread.sleep(250);
            }
            catch (InterruptedException e){
                e.printStackTrace();
            }
        }

    }
}



------------------------------------------------------------------------------------


public class CustomThread extends Thread{

    @Override
    public void run(){
        for(int i = 1; i <= 5; i++){
            System.out.print(" 1 ");
            try{
                Thread.sleep(500);
            }
            catch(InterruptedException  e){
                e.printStackTrace();
            }
        }
    }
}

