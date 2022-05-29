                                # ---- [ CRON ] ---- #
                                
                [ < GO Back](index.md)
                
## TASKS

				### LIST
										crontab -l
						
				### REMOVE
										crontab -r
						

## VALUE

					1. Minutes [0,59]
					2. Hour [0,23]
					3. Day of the month [1,31]
					4. Month [1,12]
					5. Day of the week [0,6] 														0 = Sunday
				
## EXAMPLE
				
				15	 	3 	* 	* 	1-5										Every weekday in the morning at 3:15 AM 				
			  0 		12 	14 	2 	*											Mail a birthday 
				0 		0   * 	* 	1											Every Monday 
				*/45 	* 	*		*		*											Run every 45 minutes
				* * * * * export DISPLAY=:0 && qjackctl
				 
			
