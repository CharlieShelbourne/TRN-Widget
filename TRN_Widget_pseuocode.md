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

    IF (MAC Site1)
       
       IF (Packet_Header1)
       
         RETURN True; 

       ELSEIF (Packet_Header2)
       
         RETURN True;

       ELSEIF (Packet_Header3)
       
         RETURN True;

       ELSE 
  
           RETURN TRN_Board_IPError;

       ENDIF
   
    IF (MAC site2)
        
       IF (Packet_Header1)
       
         RETURN True;

       ELSEIF (Packet_Header2)
       
         RETURN True;
        
       ELSE
         
           RETURN TRN_Board_IPError;
    
    ELSE 

         RETURN Site_Error;  
   
    ENDIF 

END 

    
ERROR CHECK(Error, Error_Code, MAc)


START 
     

      IF Error == 1

             LIGHT LED(Error,Error_code);

      ELSE IF Error Code1 == 0
       
             LIGHT LED(Comparitor(MAC));  //Mac global variable
      ELSE 
             LIGHT LED(Error,Error_code);
     
      ENDIF

END       






LIGHT_LED 

START 
     
     IF Error Code == 1

        IF Error == 1
 
           LED ON (1);

        Else 

           LED OFF (1);

        ENDIF

     ENDIF
    
     IF Error Code == 2

        IF Error == 1
 
           LED ON (2);

        Else 

           LED OFF (2);

        ENDIF

     ENDIF
              
     IF Error Code == 3

        IF Error == 1
 
           LED ON (3);

        Else 

           LED OFF (3);

        ENDIF

      ENDIF

      
     IF Error Code 4

        IF Error== 1
 
           LED ON (4);

        Else 

           LED OFF (4);
      ENDIF

       IF Error Code== 5

        IF Error == 1
 
           LED ON (5);

        Else 

           LED OFF (5);
     
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


Initialise Variables

START

     
      IF Site MAC == Site1
        
        SET IP TRN1 to ...
        SET IP TRN2 to...
        SET IP TRN3 to...
        Error Check(Error code)
        complete =1;
      ELSEIF Site MAC == Site2
  
        SET IP TRN1 to ...
        SET IP TRN2 to...
        MASK IP TRN3 
        Error Check(Error Code)
        complete =1;
      ELSE
   
        Error Check(Error Code)
        complete =0;
END 



© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
