# Reverse-Echo-Server--Network-Programming
#This program sets the communication between server and the the client and also entertains the flow of data between client and the server


package reverseecho;

/**
 *
 * @author Shivam Yadav
 */
import java.lang.*;
import java.util.*;
import java.net.*;
import java.io.*;



public class ReverseEcho {

    
    public static void main(String[] args) throws Exception {
        
        ServerSocket ss=new ServerSocket(2000);
        
        Socket stk=ss.accept();
        
        BufferedReader br=new BufferedReader(new InputStreamReader(stk.getInputStream()));
        PrintStream ps=new PrintStream(stk.getOutputStream());
        
        String msg;
        StringBuilder sb;
        do{
           msg=br.readLine();
           sb=new StringBuilder(msg);
           msg=sb.toString();
        }while(!msg.equals("dne"));
    }
        

}
class Client{
    
    
        public static void main(String[] args) throws Exception {
        Socket stk=new Socket("172.16.1.192",2000);
        
        BufferedReader Keyb=new BufferedReader(new InputStreamReader(System.in));
        BufferedReader br=new BufferedReader(new InputStreamReader(stk.getInputStream()));
        PrintStream ps=new PrintStream(stk.getOutputStream());
        
        String msg;
        
        do{
           msg=Keyb.readLine();
           ps.println(msg);
           msg=br.readLine();
           System.out.println("From Server Side"+" "+msg);
        }while(!msg.equals("dne"));
        }
}

