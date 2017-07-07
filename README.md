# TRN-Widget
Pseudo code for TRN no. Board Widget 
Author Charlie Shelbourne 07/07/2017


Main Controller 

START
     REPEAT
     
           DO Ping;
           
     UNTIL Ping complete  
     
     REPEAT
     
           DO Initialise;
           
     UNTIL Initialise complete 
     
     REPEAT

     	   DO change IP;
     
     	   REPEAT 
           	TCP protocol;
     	   UNTIL TCP protocl complete

     UNTIL Unplugged      

END      




PING 

START 
     WHILE NOT pinged

          SET 142 to incomplete;
          DO Error Check;
          ping 142 Modem;
          
     ENDWHILE
     
     SET 142 to complete;
     DO Error Check;
    
     WHILE NOTpinged

          SET 226 to incomplete;
	  DO Error Check;
          ping 224 Modem ring;
          
     ENDWHILE
     
     SET 226 to complete;
     DO Error Check;

     WHILE NOT pinged
          
          SET MT/IF to incomplete;
	  DO Error Check;
          ping Maintainer Interface;
          
     ENDWHILE
     
     SET MT/IF to complete;
     DO Error Check;

END

INITIALISE

START

     DO Get Site MAC;

     WHILE Exctract & Store incomplete
           
	   SET Error Check(incomplete);
           DO Exctract & Store;
           DO Error Check;
           
     ENDWHILE
           
     SET Error Check(complete); 

     DO Initialise Variables;

END



CHANGE IP

START 

     IF Original IP
      
        Change to TNR 1 IP;
     
     ELSE IF TRN 1 IP
  
        Change to TRN 2 IP;

     ELSE IF TRN 2 IP

        Change to TRN 3 IP;

     ELSE IF TRN 3 IP
   
        Change to TRN 1 IP;

     END IF

END 

 

TCP PROTOCOL

START  

     REPEAT
 
           SET Error Check(Incomplete);
           DO HandShake;

     UNTIL Handshake complete
   
     Error Check(complete);

     WHILE Exctract & Store Incomplete 
        
           SET Error Check(Incomplete);
           DO Extract & Store;
           DO Error Check;

     ENDWHILE 
     
          
     DO Mask;
     
     FOR 30 seconds

        DO Display; 

     END FOR

END



COMPARITOR

START 

    IF MAC
       
       IF (DATA MAC == MAC)
       
          RETURN Correct; 

       ELSE 
 
          RETURN Incorrect; 
    
       ENDIF

    ELSE IF (IP)

       IF (DATA IP == IP)
       
         RETURN Correct; 
       
       ELSE 

         RETURN Incorrect;

       ENDIF 
   
    ENDIF 

END 


    
ERROR CHECK


START 
     

      IF Error Code 1

             Error LED(1);

      ELSE IF Error Code 2
      
             Error LED(2);
 
      ELSE IF Error Code 3
       
             Error LED(Comparitor(MAC));
    
      ELSE IF Error Code 

             Error LED(comparitor(IP));
     
      ENDIF

END       





ERROR LED 

START 
     
     IF Error Code1 == 1

        IF Error Code2 == 1
 
           LED ON (1);

        Else 

           LED OFF (1);

        ENDIF

     ENDIF
    
     IF Error Code1 == 2

        IF Error Code2 == 1
 
           LED ON (2);

        Else 

           LED OFF (2);

        ENDIF

     ENDIF
              
     IF Error Code1 == 3

        IF Error Code2 == 1
 
           LED ON (3);

        Else 

           LED OFF (3);

        ENDIF

      ENDIF

      
     IF Error Code1 == 4

        IF Error Code2 == 1
 
           LED ON (4);

        Else 

           LED OFF (4);
     
        ENDIF

     ENDIF

END 



LED ON 

START 

     CASE LED no. OF

          1 : PIN 1 5V
          2 : PIN 2 5V
          3 : PIN 3 5V
          4 : PIN 4 5V
     ENDCASE


END 



LED OFF

START 

     CASE LED no. OF

          1 : PIN 1 0V
          2 : PIN 2 0V
          3 : PIN 3 0V
          4 : PIN 4 0V
     ENDCASE 

END 




