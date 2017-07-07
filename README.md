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
