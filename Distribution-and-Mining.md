# Distribution
The initial distribution of XRB is performed through manual mining limited via a captcha.  There's also an overall rate limit set by the distribution schedule.  Currently the distribution rate is 17,000 Mrai per hour.  Over 50% of distribution will be completed by the end of 2017.

Genesis account:  
**xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3**  
Landing account:  
**xrb_13ezf4od79h1tgj9aiu4djzcmmguendtjfuhwfukhuucboua8cpoihmh8byo**
Faucet account: (no more used since 2017-01-19 12:02:21 am)  
**xrb_13ezf4od79h1tgj9aiu4djzcmmguendtjfuhwfukhuucboua8cpoihmh8byo**  

The genesis balance is kept in cold storage in a bank secure box.  
Blocks move from the genesis account to the landing account once per week in order to minimize the number of live undistributed blocks.   

No portion of any of the listed accounts is reserved by anyone.  All genesis blocks will be made available to anyone via the same distribution mechanism.

# Divider  
We use a 128 bit integer to represent account balances, this is too large to present to the user so we defined a set of SI prefixes to make the numbers more accessible and avoid confusion.  The reference wallet uses Mrai as a divider.  
Grai = 1000000000000000000000000000000000, 10^33  
Mrai = 1000000000000000000000000000000, 10^30  
krai = 1000000000000000000000000000, 10^27  
 rai = 1000000000000000000000000, 10^24  
mrai = 1000000000000000000000, 10^21  
urai = 1000000000000000000, 10^18  

# Mining

Coin mining is a natural extension of proof of work cryptocurrencies in order to disseminate coins in a distributed fashion.  Unfortunately the high cost of mining in terms of hardware and energy lowers the value of the currency which is a concern to the majority of users who don't mine.

Mining is also used as a reward mechanism for maintaining integrity of proof of work algorithms.  There are many aspects to maintaining a full cryptocurrency including processing transactions, bandwidth, storage space, and building end user software.  Unfortunately mining as a reward mechanism only rewards one aspect of keeping a cryptocurrency healthy, transaction processing.  In fact miners don't need to be invested at all in the currency they're mining which gives skewed incentives.  The beneficiaries of mining unfortunately also tend to be slanted toward enthusiasts or those with capital investment in mining hardware.  The reward value for mining is not fixed with its cost, in the long term the value generated from mining might not be enough to cover the expense of using a proof of work scheme.  