# Distribution
The initial distribution of XRB was performed through manual mining limited via a captcha.  There's also an overall rate limit set by the distribution schedule. The distribution rate was 17,000 Mxrb per hour. Distribution stopped after 39% as distributed and the rest of the supply was burnt. For more info: [Tech Summary](https://raiblocks.net/page/summary.php)

Genesis account:  
**xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3**  
Landing account:  
**xrb_13ezf4od79h1tgj9aiu4djzcmmguendtjfuhwfukhuucboua8cpoihmh8byo**  
Faucet account: (no more used since 2017-01-19 12:02:21 am)  
**xrb_35jjmmmh81kydepzeuf9oec8hzkay7msr6yxagzxpcht7thwa5bus5tomgz9**  

The genesis balance is kept in cold storage in a bank secure box.  
Blocks move from the genesis account to the landing account once per week in order to minimize the number of live undistributed blocks.   

No portion of any of the listed accounts is reserved by anyone.  All genesis blocks will be made available to anyone via the same distribution mechanism.

# Divider  
We use a 128 bit integer to represent account balances, this is too large to present to the user so we defined a set of SI prefixes to make the numbers more accessible and avoid confusion.  The reference wallet uses Mxrb as a divider.  
Gxrb = 1000000000000000000000000000000000, 10^33  
Mxrb = 1000000000000000000000000000000, 10^30  
kxrb = 1000000000000000000000000000, 10^27  
 xrb = 1000000000000000000000000, 10^24  
mxrb = 1000000000000000000000, 10^21  
uxrb = 1000000000000000000, 10^18  

1 Mxrb used to be also called 1 Mrai

1 xrb is 10^24 raw

1 raw is the smallest possible division

# Mining

Coin mining is a natural extension of proof of work cryptocurrencies in order to disseminate coins in a distributed fashion.  Unfortunately the high cost of mining in terms of hardware and energy lowers the value of the currency which is a concern to the majority of users who don't mine.

Mining is also used as a reward mechanism for maintaining integrity of proof of work algorithms.  There are many aspects to maintaining a full cryptocurrency including processing transactions, bandwidth, storage space, and building end user software.  

Unfortunately mining as a reward mechanism only rewards one aspect of keeping a cryptocurrency healthy, transaction processing.  In fact miners don't need to be invested at all in the currency they're mining which gives skewed incentives.  The beneficiaries of mining unfortunately also tend to be slanted toward enthusiasts or those with capital investment in mining hardware.  The reward value for mining is not fixed with its cost, in the long term the value generated from mining might not be enough to cover the expense of using a proof of work scheme.  

Raiblocks are not generated via mining.