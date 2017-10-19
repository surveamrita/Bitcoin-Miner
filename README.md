# Bitcoin-Miner
Implemented Bitcoin Miner using Actor Model in Elixir

READ ME file for Distributed Operating Systems - Project 1
Description: This is an distributed Bitcoin mining system based on Actor Model in Elixir/Erlang.
Date: September 18th, 2017

Team members:

1. Amrita Surve, UFID: 35569083, asurve@ufl.edu
2. Sai Naveen Rachakonda, UFID: 26117198, naveen41@ufl.edu

Implementation Details:

	1. 	Work Unit:
  The application follows a Client-Server architecture and is implemented using GenServer.  
  1. Server:
  - The Server on starting up creates its own Node and Spawns 8 Work units, since its running on a 8 Core machine.
  - The Server connects with one or more clients, and sends the number of zeros for mining bitcoins to the clients.

  2. Client:
  - The Client connects to the Server 
  - On receiving the number of zeros to mine, the Client spawns 8 Work units on its own machine and generates as many bitcoins as possible. 
   
   Since both Server and Client machines have 8 cores each, the number of work units spawned is 8.

   Inside the Work Unit we are generating a 5 character string using a random string generator which is further hashed with SHA256. This generates a fixed length string of 32 digits. The total number of permutations for an alphanumeric string of 32 characters is (32)^36.

	2.	The result of running your program for
The random string is prefixed by gator_id = "asurve;" and the no of zeros(k) is given as 4.

escript ./project1 4
asurve;d0nLd    0000BC730D930FBD700863809F66C4E14AB55C2C23BAF11A415A3990E9FD176F
asurve;ecZq8    00000775EEA33EAAF25A54E5F4A5509FF28B65DA13F981987D68258BBE3C4F1A
asurve;QISTQ    00002BEFE6A382A93015C5339032F2B4608307DDF1823873DBDFEE99E6033C67
asurve;nZ9g0    0000DBC9183CDC234051DBBD430C24D54DFBD2A8BC632DA1A567AB86C8CE8EC5
asurve;5zk5o    0000FA9311CD9AAB44CBD32B08016AC6D99140E92365A984B09304CA0A66762E
asurve;LGgnG    00006B46752D74B838F7F5E1DF8AD43C74F6F71DCF083E5F03863E17DA25280A
asurve;MHuMW    0000227EE775A0036D4180B29BD0ADA1D0940786B0C2D10A9FD317F19EBA3328
asurve;SFBND    000072A388EE43D176D7E51B7D28DEB23590A2F4BAB808220E644718D105CBA0
asurve;aNBTt    00009B3067081AD46C4CAF0857C52873DC433D1932B9755F2047184D372D2EB5
asurve;BnP14    00007FF13053C94F87555455BAB5403ACFDD4376AF26A3350FD2F30638ED314B
asurve;u9Peh    000065DB0498524E01554E9AD470EB4C4F7C42730B20A9EFB23232CAABC2265D
asurve;xsQo8    00009B85322234D323962BF9A2E29DA4CDE04893A2D0AF8F8AA93443FB4624FA
asurve;VtU0X    0000C4A9FEE4F96E727D6007E10B7BB33AF9F6730784E7882C8277F2F23071F8
asurve;4AEDY    0000E251F1E77A78616EDD697A4785ECEA2E5F29ACF84384AE8F6948D963ED28
asurve;Coqky    0000B7C4950ED890F28C695BCD819B18A224F390AA37E9DC8684758E7886F4F3
asurve;aydbv    0000ADC24D049154F9AB0FF8CD7E03BB12E057A01CCDC65339327094DBCDEC43
asurve;hA1YF    0000752D539680D96BF01E278BC49E62468DAC6EC8F01C1F7AF6E648CE6D921A
asurve;1VPRb    000013662459F05EDCC948935DA0B637D0B2E0CF218B2497A2E3F1B05C4BACEE
asurve;rnpJL    0000EE99FB097AC914D76F6EC6A872B222C0FA30F40ACAEC96314FF585403DAA
asurve;e9ARk    0000F1425039C1B935558F155E9464A57419DE135FE1DE13DF287161ECF4FECA
asurve;FEhtf    000095EF9CA57222C91763C1F644CF5BD90CB19C8F93EB082B6A3E2600551325
asurve;twDER    0000731E939C023D0B63E32AB5A5918B603FE46308591F9AE638EB9DCA71732F
asurve;BW7nj    00004D6FC073ED2CBC34854983A660A086ABE66318922B08DFDF2560C2A15DDD
asurve;ty8SF    0000DE29AE9EB01D9814D92AE43D055BE54C75C72345D011E34C2648EC4636D3


3. 	The run time of the program on a Intel i7 machine with 2 cores and 4 threads(4 virtual cores with hyper threading) at 2.4 GHz is given below:

The program is ran on a 8 core machine and the CPU utilization is found to be 756% and the no of cores is 7.56		

$ time ./project1 5
asurve;iYD3W    000001ED17536C01C0C0E026CBF9A06A736FD9C8314787586D83915EB2127DEE
asurve;plHvS    00000B744DD49B19AC28D90609DB86CA8236488281FB725E8A2612D6F300F288
asurve;vRSZD    00000C88F2CF5CB536DDD8B66CFE551B05E87CB6835D62C42D164940147EEE31

real    5m54.426s
user    0m46.881s
sys     0m0.000s

Total CPU time = 0m46.881s = 46.881 seconds
Real Time = 5m54.426s = 354.426 seconds
The ratio of CPU time to Real time = 7.56
		
4. 	The largest number of working machines we tested our code on was with 5 machines (4 miners and one master).
	
