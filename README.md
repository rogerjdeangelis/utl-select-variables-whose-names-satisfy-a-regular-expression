# utl_select_variables_whose_names_satisfy_a_regular_expression
    Select variables whose names satisfy a regular expression                                                                           
                                                                                                                                        
    github                                                                                                                              
    https://tinyurl.com/yaaht7nr                                                                                                        
    https://github.com/rogerjdeangelis/utl-select-variables-whose-names-satisfy-a-regular-expression                                    
                                                                                                                                        
    Varlist macro by                                                                                                                    
     Author: Søren Lassen, s.lassen@post.tele.dk                                                                                        
                                                                                                                                        
    see for macros                                                                                                                      
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                                          
                                                                                                                                        
    Related to                                                                                                                          
    https://communities.sas.com/t5/SAS-Programming/why-is-my-drop-not-working/m-p/503030                                                
                                                                                                                                        
                                                                                                                                        
    Problem: Drop date and time variables that have sufix '_D' and '_DT'                                                                
                                                                                                                                        
                                                                                                                                        
    INPUT                                                                                                                               
    =====                                                                                                                               
                                                                                                                                        
    WORK.HAVE total obs=19                                                                                                              
                                                                                                                                        
         BEG_D      END_D             BEG_DT            END_DT    NAME       AGE                                                        
                                                                                                                                        
     09OCT2016  09OCT2016   09OCT16:00:00:00  09OCT16:00:00:00    Alfred      14                                                        
     09OCT2016  09OCT2016   09OCT16:00:00:00  09OCT16:00:00:00    Alice       13                                                        
     09OCT2016  09OCT2016   09OCT16:00:00:00  09OCT16:00:00:00    Barbara     13                                                        
     09OCT2016  09OCT2016   09OCT16:00:00:00  09OCT16:00:00:00    Carol       14                                                        
     09OCT2016  09OCT2016   09OCT16:00:00:00  09OCT16:00:00:00    Henry       14                                                        
     09OCT2016  09OCT2016   09OCT16:00:00:00  09OCT16:00:00:00    James       12                                                        
     ....                                                                                                                               
                                                                                                                                        
    EXAMPLE OUTPUT                                                                                                                      
    --------------                                                                                                                      
                                                                                                                                        
    WORK.WANT total obs=19                                                                                                              
                                                                                                                                        
       NAME       AGE                                                                                                                   
                                                                                                                                        
       Alfred      14                                                                                                                   
       Alice       13                                                                                                                   
       Barbara     13                                                                                                                   
       Carol       14                                                                                                                   
       Henry       14                                                                                                                   
       James       12                                                                                                                   
                                                                                                                                        
                                                                                                                                        
                                                                                                                                        
    PROCESS                                                                                                                             
    =======                                                                                                                             
                                                                                                                                        
    data want;                                                                                                                          
      set have(drop=%utl_varlist(have,prx=/\_D/i));                                                                                     
    run;quit;                                                                                                                           
                                                                                                                                        
    *                _               _       _                                                                                          
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _                                                                                   
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |                                                                                  
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |                                                                                  
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|                                                                                  
                                                                                                                                        
    ;                                                                                                                                   
                                                                                                                                        
                                                                                                                                        
    data have;                                                                                                                          
                                                                                                                                        
      retain beg_d end_d 20736  beg_dt end_dt 1791590400;                                                                               
      format beg_d end_d date9.  beg_dt end_dt datetime18.;                                                                             
      set sashelp.class(keep=name age);                                                                                                 
                                                                                                                                        
    run;quit;                                                                                                                           
                                                                                                                                        
                                               
                                                                                                               
                                             
