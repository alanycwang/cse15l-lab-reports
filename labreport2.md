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
}```

First Test:
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-01-30%20at%208.29.28%20AM.png)
 - Calls ```handleRequest`` with url ```"/add-message?s=test"``
 - Changes ```message``` from empty string to ```"test\n"```
 
Second Test:
![](https://raw.githubusercontent.com/alanycwang/cse15l-lab-reports/main/Screen%20Shot%202023-01-30%20at%208.29.43%20AM.png)
 - Calls ```handleRequest`` with url ```"/add-message?s=12345"```
 - Changes ```message``` from ```"test\n"``` to ```"test\n12345\n"```
