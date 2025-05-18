# SI_2025_lab2_233104

Ристе Ѓорѓиев, 233104
# 2.
![Editor _ Mermaid Chart-2025-05-18-000754](https://github.com/user-attachments/assets/34a159f3-b011-44ca-9f3d-104c4885121a)


# 3.

За да ја пресметаме цикломатската комплексност ја користиме формулата CC = E - N 2P, 
така што:
ги броиме сите if, for, while, case, catch итн.
10 if услови
2 for циклуси

7 основни одлуки
4 логички оператори => 7 + 4 = 11
CC => 11 + 1 = 12


# Тест случаи според критериумот Every statement

//test1
        Item item1 = new Item("Book", 1, 100, 0.0);
        double result1 = SILab2.checkCart(List.of(item1), "1234567812345678");
        double expected1 = 200.0;

        if (result1 != expected1){
            throw new RuntimeException("Test 1 failed! Expected " + expected1);
        }

        //test2
        Item item2 = new Item("Shoes", 2, 100, 0.5);

        double result2 = SILab2.checkCart(List.of(item2), "1234567812345678");
        double expected2 = 100.0;

        if (result2 != expected2){
            throw new RuntimeException("Test 2 failed! Expected " + expected2);
        }

        //test3
        Item item3 = new Item("TV", 2, 350, 0.0);
        double results3 = SILab2.checkCart(List.of(item3), "1234567812345678");
        double expected3 = 670.00;
        if (results3 != expected3){
            throw new RuntimeException("Test 3 failed! Expected " + expected3);
        }

        //test4

        try {
            Item item4 = new Item("Pen", 1, 10, 0.0);
            SILab2.checkCart(List.of(item4), "1234abc812345");
            throw new RuntimeException("Test 4 failed: expected exception for invalid card number");
        } catch (RuntimeException ex){
            if (!ex.getMessage().equals("Invalid item!")){
                throw new RuntimeException("Test 4 failed: wrong exception message");
            }
        }

        //test5
        try {
            Item item5 = new Item(null, 1, 10, 0.0);
            SILab2.checkCart(List.of(item5), "1234567812345678");
            throw new RuntimeException("Test 5 failed: expected exception for invalid card number");
        } catch (RuntimeException ex){
            if (!ex.getMessage().equals("Invalid item!")){
                throw new RuntimeException("Test 5 failed: wrong exception message");
            }
        }

# Тест случаи според критериумот Every path

//A:
        price > 300
        Item itemA = new Item("Laptop", 1, 350, 0.0);
        double resultA = SILab2.checkCart(List.of(itemA), "1234567812345678");
        double expectedA = 320.0;
        if (resultA != expectedA){
            throw new RuntimeException("MC Test A failed: expected " + expectedA + " but got " + resultA);
        }

        //B: discount > 0
        Item itemB = new Item("DiscountItem", 1, 100, 0.2);
        double resultB = SILab2.checkCart(List.of(itemB), "1234567812345678");
        double expectedB = 50.0;
        if (resultB != expectedB){
            throw new RuntimeException("MC Test B failed: expected " + expectedB + " but got " + resultB);
        }

        //C: quantity > 10
        Item itemC = new Item("BulkItem", 11, 10, 0.0);
        double resultC = SILab2.checkCart(List.of(itemC), "1234567812345678");
        double expectedC = 80.0;
        if (resultC != expectedC){
            throw new RuntimeException("MC Test C failed: expected " + expectedC + " but got " + resultC);
        }

        //A=false, B=false, C=false
        Item itemD = new Item("NormalItem", 1, 100, 0.0);
        double resultD = SILab2.checkCart(List.of(itemD), "1234567812345678");
        double expectedD = 100.0;
        if (resultD != expectedD){
            throw new RuntimeException("MC Test A failed: expected " + expectedD + " but got " + resultD);
        }

# 4.

За да се постигне овој критериум, за Every Statement критериумот треба да има 6 test
case-ови, а за Multiple Conditions треба да има. Ова е поради тоа што треба да провериме 
ако имаме нормален тек на програмата, треба да ги провериме дали сите if случаи се точни, 
сите exceptions и сите јамки. А за Multiple Conditions имаме 4 поради тоа што имаме еден 
if случај со три под случаи, кои се поврзани со логичко или, така што треба да ги провериме сите 4 комбинации.

