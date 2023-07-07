# IT-Sec Exercise 2
## Mario Hadorn Oliver Aemmer
2. 
```
import java.io.*;  
import java.util.Scanner;  
  
public class main {  
  
    public static String shift (String string_to_shift, int shift_amount) {  
  
        string_to_shift = string_to_shift.toLowerCase();  
        char[] string_chars = string_to_shift.toCharArray();  
  
        String shifted_string = "";  
  
        for (int c : string_chars) {  
            if(c + shift_amount > 122 ){  
                c = 96 + (c + shift_amount) % 122;  
            } else {  
                c += shift_amount;  
            }  
            shifted_string += Character.toString(c);  
        }  
  
        return shifted_string;  
    }  
  
    public static void main(String args[]) throws IOException{  
  
        Scanner sc = new Scanner(System.in);  
  
        System.out.println("Shift amount: ");  
        int shift_amount = Integer.parseInt(sc.nextLine());  
        System.out.println("String to shift: ");  
        String string_to_shift = sc.nextLine();  
  
        String shifted_string = shift(string_to_shift, shift_amount);  
  
        System.out.println(shifted_string);  
  
    }  
}
```

3. ARENA and RIVER both encrypt to EVIRE
4. 
	1. 127’882’883 years
	2. Because of frequency analysis
5.  10110 00101 11001 01001 00111

