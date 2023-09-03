import java.util.Scanner;
class Solution {


    public static int RomanToInt(String RomanNumber) throws Exception {
        return switch (RomanNumber){
            case "I" -> 1;
            case "II" -> 2;
            case "III" -> 3;
            case "IV" -> 4;
            case "V" -> 5;
            case "VI" -> 6;
            case "VII" -> 7;
            case "VIII" -> 8;
            case "IX" -> 9;
            case "X" -> 10;
            default -> throw new Exception("Oh no!!!");
        };}

    public static String intToRoman(int num) {
        String[] hundreds = {"", "C"};
        String[] tens = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
        String[] ones = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};
        return hundreds[(num % 1000) / 100] + tens[(num % 100) / 10] + ones[num % 10];
    }
    public static String calculateRome(String[] Array) throws Exception{
        int first = RomanToInt(Array[0]);
        int second = RomanToInt(Array[2]);
        return switch (Array[1]) {
            case "+" -> intToRoman(first + second);
            case "-" -> intToRoman(first - second);
            case "*" -> intToRoman(first * second);
            case "/" -> intToRoman(first / second);
            default -> {
                System.out.println("Введен знак операции, отличный от допустимого (+,-,* или /)");
                System.exit(0);
                throw new Exception("Oh, no!!!");}
        };}

    public static int calculate(String[] Array) throws Exception {
        int first = Integer.parseInt(Array[0]);
        int second = Integer.parseInt(Array[2]);

        if (first <1 || first >10 || second >10 || second <1){
            System.out.println("Одно или оба значения не находятся в промежутке 1 - 10");
            System. exit(0);}

        return switch (Array[1]) {
            case "+" -> first + second;
            case "-" -> first - second;
            case "*" -> first * second;
            case "/" -> first / second;
            default -> {
                System.out.println("Введен знак операции, отличный от допустимого (+,-,* или /)");
                System.exit(0);
                throw new Exception("Oh, no!!!");
            }
        };}

        public static void main(String[] args) {
        System.out.println("Пожалуйста, введите данные для рассчета используя пробел между значениями и знаком.\nПри вводе римских цифр отрицательный результат не допускается.");
        Scanner in = new Scanner(System.in);
        String operation = "";
        do {
            String str = in.nextLine();
            String[] newType = str.split(" ");
            operation = newType[1];

            boolean isRomeFirst = newType[0].contains("I") || newType[0].contains("V") ||  newType[0].contains("X");
            boolean isRomeSecond = newType[2].contains("I") ||  newType[2].contains("V") ||  newType[2].contains("X");

            if(isRomeFirst && isRomeSecond){
                try {
                    String answer = calculateRome(newType);
                    System.out.println(answer);
                } catch (Exception e) {
                    System.out.println("Введеные данные не находятся в промежутке 1 - 10, либо скомбинированы, либо не разделены пробелом");
                    System.exit(0);
                }
            }
            else {
                try {
                    int answer = calculate(newType);
                    System.out.println(answer);
                } catch (Exception e) {
                    System.out.println("Пожалуйста, введите верное значение переменной\nПожалуйста, вводите переменные через пробел");
                }
            }
        }while (!operation.equals("q"));
    }}
