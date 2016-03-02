# Distribution
The initial distribution of blocks is performed through manual mining limited via a captcha.  There's also an overall rate limit set by the distribution schedule.

Distribution schedule:  
Year 1: 2^127 50%  
Year 2: 2^126 25%  
Year 3: 2^125 13%  
Year 4: 2^124 6.3%  
Year 5: 2^124 3.1%  
Year 6: 2^123 1.6%  
Year 7: 2^122 0.8%  
Year 8: 2^122 0.8%  

Blocks will be put in to the faucet on a 1 hour interval in equal proportions. 1 distribution year is 2^25 seconds which is approximately one calendar year.

Distribution start time: 1443657600s after unix epoch  
Genesis account:  
**xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3**  
Blocks move from the genesis account to the landing account once per week.  
Landing account:  
**xrb_13ezf4od79h1tgj9aiu4djzcmmguendtjfuhwfukhuucboua8cpoihmh8byo**  
Blocks move from the landing account to the faucet on a fixed interval less than a week.  
Faucet account:  
**xrb_35jjmmmh81kydepzeuf9oec8hzkay7msr6yxagzxpcht7thwa5bus5tomgz9**  

No portion of any of the listed accounts is reserved by anyone.  All genesis blocks will be made available to anyone via the same distribution mechanism.

# Mining

Coin mining is a natural extension of proof of work cryptocurrencies in order to disseminate coins in a distributed fashion.  Unfortunately the high cost of mining in terms of hardware and energy lowers the value of the currency which is a concern to the majority of users who don't mine.

Mining is also used as a reward mechanism for maintaining integrity of proof of work algorithms.  There are many aspects to maintaining a full cryptocurrency including processing transactions, bandwidth, storage space, and building end user software.  Unfortunately mining as a reward mechanism only rewards one aspect of keeping a cryptocurrency healthy, transaction processing.  In fact miners don't need to be invested at all in the currency they're mining which gives skewed incentives.  The beneficiaries of mining unfortunately also tend to be slanted toward enthusiasts or those with capital investment in mining hardware.  The reward value for mining is not fixed with its cost, in the long term the value generated from mining might not be enough to cover the expense of using a proof of work scheme.  