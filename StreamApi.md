package FunctionalInterface;

import java.lang.reflect.Array;
import java.math.BigDecimal;
import java.util.*;
import java.util.regex.Pattern;
import java.util.stream.Collectors;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class StreamApiPractice {
    static void main(String[] args) {

        // ==============================
        // Q1. Given a sentence, find the word that has the highest length
        // ==============================

//        String s1="I am learning java";
//        String ans=Arrays.stream(s1.split(" "))
//                .max(Comparator.comparing(String::length)).get();
//        System.out.println(ans);

        // ==============================
        // Q2. Remove duplicates from the string and return it
        // ==============================

//        String s="dabcadefg";
//        s.chars().distinct().mapToObj(c->(char)c).forEach(System.out::print);

        // ==============================
        // Q3. Find the word that has the second highest length
        // ==============================

//        String s1="I am learning Streams Api in java";
//        String ans=Arrays.stream(s1.split(" "))
//                .sorted(Comparator.comparing(String::length).reversed())
//                .skip(1).findFirst().get();
//        System.out.println(ans);

        // ==============================
        // Q4. Find the 2nd highest length (count) of a word in a sentence
        // ==============================

//        String s1 = "I am learning Streams Api in java";
//        int ans = Arrays.stream(s1.split(" "))
//                .map(String::length)
//                .sorted(Comparator.reverseOrder())
//                .skip(1).findFirst().get();
//        System.out.println(ans);

        // ==============================
        // Q5. Given a sentence, find the occurrence of each word
        // ==============================

//        String s1 = "I am learning Streams java Api in java";
//        Map<String,Long> hm = Arrays.stream(s1.split(" "))
//                .collect(Collectors.groupingBy(s->s, HashMap::new, Collectors.counting()));
//        System.out.println(hm);

        // ==============================
        // Q6. Given a sentence, find words having exactly N vowels
        // ==============================

//        String s1 = "I am learning Streams java Api in java";
//        int n=2;
//        Arrays.stream(s1.split(" "))
//                .filter(s->s.replaceAll("[^aeiouAEIOU]","").length()==n)
//                .forEach(System.out::println);

        // ==============================
        // Q7. Divide a list of integers into even and odd numbers
        // ==============================

//        int[] arr={1,2,3,4,5,6,7,8,9,11,13,16};
//        List<Integer> ls = Arrays.stream(arr).boxed().toList();
//        Map<Boolean,List<Integer>> hm = ls.stream()
//                .collect(Collectors.groupingBy(x->x%2==0));
//        System.out.println(hm);

        // ==============================
        // Q8. Given a word, find the occurrence of each character
        // ==============================

//        String s="Missipiao";
//        Map<String,Long> hm = Arrays.stream(s.split(""))
//                .collect(Collectors.groupingBy(x->x, Collectors.counting()));
//        System.out.println(hm);

        // ==============================
        // Q9. Sort an array of integers
        // ==============================

//        int[] arr={172,2,3,4,5};
//        Arrays.stream(arr).boxed().sorted().forEach(System.out::print);

        // ==============================
        // Q10. Find sum of distinct elements in an array
        // ==============================

//        int[] arr={1,2,3,4,2};
//        System.out.println(Arrays.stream(arr).boxed()
//                .distinct().reduce(Integer::sum).get());

        // ==============================
        // Q11. Find the first non-repeated character
        // ==============================

//        String s="HHelelo World";
//        Map<Character,Long> map = s.chars().mapToObj(c->(char)c)
//                .collect(Collectors.groupingBy(c->c, LinkedHashMap::new, Collectors.counting()));
//        char ch = map.entrySet().stream()
//                .filter(e->e.getValue()==1 && e.getKey()!=' ')
//                .map(Map.Entry::getKey)
//                .findFirst().get();
//        System.out.println(ch);

        // ==============================
        // Q12. Find the first repeated character
        // ==============================

//        String s="Hello World";
//        Map<Character,Long> map = s.chars().mapToObj(c->(char)c)
//                .collect(Collectors.groupingBy(c->c, LinkedHashMap::new, Collectors.counting()));
//        char ch = map.entrySet().stream()
//                .filter(e->e.getValue()>1 && e.getKey()!=' ')
//                .map(Map.Entry::getKey)
//                .findFirst().get();
//        System.out.println(ch);

        // ==============================
        // Q13. Group integers by range (0–9, 10–19, etc.)
        // ==============================

//        int arr[]={2,3,10,14,20,24,30,34,40,44,50,54};
//        Map<Integer,List<Integer>> hm = Arrays.stream(arr).boxed()
//                .collect(Collectors.groupingBy(n->n/10*10));
//        System.out.println(hm);

        // ==============================
        // Q14. Convert list of strings to list of integers (only numeric values)
        // ==============================

//        List<String> ls = Arrays.asList("as","123","456","oi12");
//        List<Integer> list = ls.stream()
//                .filter(s->s.matches("\\d+"))
//                .map(Integer::parseInt).toList();
//        System.out.println(list);

        // ==============================
        // Q15. Find the product of first two elements in an array
        // ==============================

//        int [] arr={12,20,30,40};
//        int ans = Arrays.stream(arr).boxed()
//                .limit(2).reduce(1,(a,b)->a*b);
//        System.out.println(ans);

        // ==============================
        // Q16. Group anagrams from a list of strings
        // ==============================

//        List<String> ls = Arrays.asList("eat","tea","tan","ate","nat","bat");
//        Collection<List<String>> list = ls.stream()
//                .collect(Collectors.groupingBy(
//                        s->Arrays.stream(s.split("")).sorted().toList()
//                )).values();
//        System.out.println(list);

        // ==============================
        // Q17. Multiply alternate numbers in an array
        // ==============================

//        int[] arr={1,2,3,4,5,6,5};
//        int ans = IntStream.range(0, arr.length)
//                .filter(i->i%2==0)
//                .map(i->arr[i])
//                .reduce(1,(a,b)->a*b);
//        System.out.println(ans);

        // ==============================
        // Q18. Multiply 1st & last, 2nd & 2nd last elements
        // ==============================

//        int[] arr={1,2,3,4,5,6,5};
//        List<Integer> ls = IntStream.range(0, arr.length/2)
//                .map(i->arr[i]*arr[arr.length-i-1])
//                .boxed().toList();
//        System.out.println(ls);

        // ==============================
        // Q19. Move all zeros to the beginning of the array
        // ==============================

//        int[] arr={5,0,1,1,0,3,0,0};
//        List<Integer> result = Arrays.stream(arr).boxed()
//                .collect(Collectors.partitioningBy(x->x!=0))
//                .values().stream().flatMap(List::stream).toList();
//        System.out.println(result);

        // ==============================
        // Q20. Check if array contains all distinct elements
        // ==============================

//        int[] arr={4,0,1,2,4,3};
//        boolean ans = Arrays.stream(arr).boxed()
//                .collect(Collectors.groupingBy(x->x,Collectors.counting()))
//                .values().stream().noneMatch(c->c>1);
//        System.out.println(ans);

        // ==============================
        // Q21. Group strings based on middle character
        // ==============================

//        String arr[]={"wrn","apa","spa","uji","tjp","brb","tjp"};
//        Map<String,List<String>> map = Arrays.stream(arr)
//                .collect(Collectors.groupingBy(s->s.substring(1,2)));
//        System.out.println(map);

        // ==============================
        // Q22. Find the sum of all elements in a list
        // ==============================

//        List<Integer> ls = Arrays.asList(1,23,4,4,5);
//        int ans = ls.stream().mapToInt(Integer::intValue).sum();
//        System.out.println(ans);

        // ==============================
        // Q23. Sort a list of strings alphabetically
        // ==============================

//        List<String> ls = Arrays.asList("Ram","Shyam","Moha","Saurav","Mam");
//        System.out.println(ls.stream().sorted().toList());

        // ==============================
        // Q24. Convert a list of integers to their squares
        // ==============================

//        List<Integer> ls = Arrays.asList(1,23,4,4,5);
//        System.out.println(ls.stream().map(x->x*x).toList());

        // ==============================
        // Q25. Find distinct odd numbers from a list
        // ==============================

//        List<Integer> ls = Arrays.asList(1,2,3,3,4,4,5,9,9,7);
//        System.out.println(ls.stream().distinct().filter(x->x%2!=0).toList());

        // ==============================
        // Q26. Find the union of two lists of integers
        // ==============================

//        List<Integer> ls = Arrays.asList(1,2,3,3,4,4);
//        List<Integer> ls1 = Arrays.asList(5,9,9,7);
//        List<Integer> result = Stream.concat(ls.stream(), ls1.stream())
//                .distinct().toList();
//        System.out.println(result);

        // ==============================
        // Q27. Find the kth smallest element in a list
        // ==============================

//        List<Integer> ls = Arrays.asList(2,1,4,6,2,5);
//        int k=2;
//        int ans = ls.stream().sorted().skip(k-1).findFirst().get();
//        System.out.println(ans);

        // ==============================
        // Q28. Remove all non-numeric characters from strings
        // ==============================

//        List<String> ls = Arrays.asList("a123nfh2","123bdg45dg","lk876gdd54");
//        Pattern pattern = Pattern.compile("[^0-9]");
//        System.out.println(ls.stream()
//                .map(s->pattern.matcher(s).replaceAll(""))
//                .toList());

        // ==============================
        // Q29. Find strings containing only digits
        // ==============================

//        List<String> abc = Arrays.asList("123","abc","123abc","45");
//        abc.stream().filter(x->x.matches("\\d+")).forEach(System.out::println);

        // ==============================
        // Q30. Convert list of strings to uppercase
        // ==============================

//        List<String> ls = Arrays.asList("hello i am anshu","wordsf","jdjhhsdgy");
//        System.out.println(ls.stream().map(String::toUpperCase).toList());
    }
}
