import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the substrCount function below.
    static long substrCount(int n, String s) {

        char[] stringAsArray=s.toCharArray();

        
        long specialStringCounter=0;
        long sameCharacters=1;
        long sameCharactersBefore=0;
        long sameCharactersBeforeMiddle=0;

        Character characterBeforeMiddle=Character.MIN_VALUE;


        for(int stepper=0;stepper<n; stepper++){
            //Minden elemet megnezunk hogy az utana levovel azonos e, es szamoljuk azt
            if(stepper<n-1 && stringAsArray[stepper]==stringAsArray[stepper+1]){
                sameCharacters++;
            }else{
                //Ha egy azonos karakterekbol allo sorozat elotti karakterek megegyeznek a kozepso kulonbozo karakter utani karakterekkel, akkor annyit adunk a specialis karakterszamlalohoz, ahany ilyen karakter van a kozepso elvalszto karakter utan, de legfeljebb annyit mint amennyi elotte volt
                if(stringAsArray[stepper]==characterBeforeMiddle)
                    specialStringCounter+=sameCharactersBeforeMiddle>sameCharacters?sameCharacters:sameCharactersBeforeMiddle;
                    //Ezutan alapertekbe allitjuk a valtozokat
                    characterBeforeMiddle=Character.MIN_VALUE;
                    sameCharactersBeforeMiddle=0;
                //Ha az azonos karakterekbol allo sorozat utan csak 1 kulonbozo betu van fenall a lehetosege annak hogy egy olyan specialis Stringgel van dolgunk aminek csak a kozepe mas. Ezert a kulonbozo kozepso karakter elotti karaktertipust es annak elofordulasi mennyiseget elemtnjuk hogy keseobb kiszamolhassuk belole hogy hany szimmetrikus specialis sztring epitheto meg ugy hogy ez az egyke mas karakter a kozeppontja       
                if(sameCharacters==1 && stepper>0){
                    characterBeforeMiddle=stringAsArray[stepper-1];
                    sameCharactersBeforeMiddle=sameCharactersBefore;
                }
                //Elmentjuk hogy az itt talalt azonos karakterekbol allo sorozat hany tagbol allt(nem tudom szukseges e, lehet csak regi maradvany)
                sameCharactersBefore=sameCharacters;

                //Azonos karakterekbol allo sorozat eseten igy kell kiszamolni a hosszbol hogy hany specialis sztringet lehet belole kirekni(Partial Sum)
                specialStringCounter+=(sameCharacters*(sameCharacters+1))/2;

                //Azonos karakterekbol allo sorozat szamlalojanak alaphelyzetbe allitasa
                sameCharacters=1;
            }

        }
        return specialStringCounter;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        String s = scanner.nextLine();

        long result = substrCount(n, s);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}
