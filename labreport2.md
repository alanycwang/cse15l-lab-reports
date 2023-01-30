# Lab Report 2

## Part 1: StringServer
```import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {

    String message = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                    message += parameters[1] + "\n";
                    return message;
            }
        }
        return "404 Not Found";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0) {
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
``` 

First Test:  
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-01-30%20at%208.29.28%20AM.png)
 - Calls ```handleRequest``` with url ```"/add-message?s=test"```
 - Changes ```message``` from empty string to ```"test\n"```
 
Second Test:  
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-01-30%20at%208.29.43%20AM.png)
 - Calls ```handleRequest``` with url ```"/add-message?s=12345"```
 - Changes ```message``` from ```"test\n"``` to ```"test\n12345\n"```

## Part 2: List Methods
I created a new class: ```class AChecker implements StringChecker``` to test the filter method. AChecker's checkString method returns true when the given string's first char is ```a```:  
```
class AChecker implements StringChecker {
    public boolean checkString(String s) {
        return (s.charAt(0) == 'a');
    }
}
```

Failure Inducing Input:  
```
public void testFilter() {
    StringChecker sc = new AChecker();
    ArrayList<String> test1 = new ArrayList<String>();
    test1.add("a");
    test1.add("laksdjf");
    test1.add("aljkwjes");
    ArrayList<String> ans1 = new ArrayList<String>();
    ans1.add("a");
    ans1.add("aljkwjes");
    assertTrue(ans1.equals(ListExamples.filter(test1, sc)));
}
```

Working Input:
```
public void testFilter() {
    StringChecker sc = new AChecker();
    ArrayList<String> test1 = new ArrayList<String>();
    test1.add("a");
    test1.add("laksdjf");
    test1.add("a");
    ArrayList<String> ans1 = new ArrayList<String>();
    ans1.add("a");
    ans1.add("a");
    assertTrue(ans1.equals(ListExamples.filter(test1, sc)));
}
```

Test Screenshot:  
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-01-30%20at%2012.41.12%20PM.png)

When filtering the given list, the original code adds every filtered object to the front of the list, essentially creating the reverse of the expected list. Changing ```add(0, s);``` to  ```add(s);``` makes the program add the fitlered object to the end of the list, which results in the correct ordering.

Original Code:  
```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
}
```

Fixed Code:
```static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
}
```
  
## Part 3: Something that I learned
After only using Github Desktop for the last two years, I leaned how to use actual terminal commands to create and manage my repositories. Although I still prefer to use the GUI, I find the git commands useful in some situations, especially when I already have a terminal open and don't want to open up the desktop app.
