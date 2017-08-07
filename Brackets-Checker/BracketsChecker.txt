
import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.Stack;

public class BracketsChecker {

    public static void main(String[] args) throws FileNotFoundException, IOException 
	{
        
        FileReader fileReader = new FileReader("HelloWorld.txt");
        BufferedReader bufferedReader = new BufferedReader(fileReader);
        
        Stack<Character> openBrackets = new Stack<Character>();
        Stack<Character> closingBrackets = new Stack<Character>();
        
        String line = bufferedReader.readLine();
   
        int lineCounter = 0; 
        
        while(line!=null){
            
            lineCounter++;
            String[] words = line.split(" ");
            
            for(int i=0; i<words.length; i++){
                for(int j=0; j<words[i].length(); j++){
                    char character = words[i].charAt(j);
                    switch(character){
                        case '{': openBrackets.add('}'); break;
                        case '(': openBrackets.add(')'); break;
                        case '[': openBrackets.add(']'); break;
                        case '}': 
                        case ')': 
                        case ']': 
                            if(!openBrackets.isEmpty()){
                                if(openBrackets.pop()!= character)
                                    System.out.println("'"+character+"' Unmatched bracket found: 

at line "+lineCounter);
                            }else{
                                System.out.println("'"+character+"' closing bracket without 

opening bracekt found: at line "+lineCounter);
                            }break;    
                    }
                }
            }
            
            line = bufferedReader.readLine();
        }
        
        while(!openBrackets.isEmpty()){
            openBrackets.pop();
            System.out.println("Opening bracket without closing bracekt found: at line 

"+lineCounter--);
        }
        
    }
    
}
