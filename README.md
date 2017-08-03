# bootcamp

import java.util.Stack;

public class StackOrder {

    public static void main(String[] args){

        int max;
        boolean continueSort = true;

        Stack<Integer> stack = new Stack<Integer>();
        Stack<Integer> stack1 = new Stack<Integer>();

        stack.add(1);
        stack.add(100);
        stack.add(5);
        stack.add(2);
        stack.add(523);
        stack.add(2);

        System.out.println(stack);

        while(continueSort){
            int size = stack.size();
            int temp = stack.pop();
            int s = size;
            int count = 0;

            while (size>1){
                if(temp>=stack.peek()){
                    stack1.add(temp);
                    temp = stack.pop();
                    count++;
                }
                else{
                    stack1.add(stack.pop());
                }
                size--;
            }

            if(count == s-1)
                continueSort = false;

            stack1.add(temp);

            while (s>0){
                stack.add(stack1.pop());
                s--;
            }
        }

        System.out.println(stack);

    }



}
