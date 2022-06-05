# uniswap-trading-nodejs

![image](https://user-images.githubusercontent.com/69389020/172056392-70ffec45-83fb-41eb-8686-5ce532a17a85.png)




![image](https://user-images.githubusercontent.com/69389020/172056440-9a5452f5-ba0e-40cd-8b6a-0f25adfc425d.png)
![image](https://user-images.githubusercontent.com/69389020/172056472-4c404181-fff3-4a7a-a4e7-15b14ed7fb6e.png)


![image](https://user-images.githubusercontent.com/69389020/172056500-2d4e51cb-6963-4966-a276-5e35cdfa9aaa.png)
constant product formula with this formula the product of the results of the two assets
of the pair must always be equal to the same value
for example if there is 10 ether and a 20,000 dai in reserve before trading the product is
equal to 200 000.

ETH_RESERVE_AFTER *DAI_RESERVE_AFTER=200000

after trading the product must be the same if a trader wants to buy one ether after the trade we will have
nine ether left in the reserve so the equation we haveto solve is
(ETH_RESERVE_BEFORE-ETH_BOUGHT)*(DAI_RESERVE_BEFORE+DAI_SOLD)=200000
(10-1)*(20000+DAI_SOLD)=200000
DAI_SOLD=200000/9-20,000=2,222

nine times dai reserved after equal two hundred thousand so we can rearrange this to get the
value for the dai provided by the trader and we find 2222 dai so even though the initial price of
ether was 2000 dai the trader ends up paying 2222 dai for his 1 eth
 the difference is what we call sleepage the more a trader uses the liquidity of a pair the bigger the slippage and the worse the price if a trader really wants to trade a very large amount the slippage becomes exponential which will act as a deterrent and guarantees that nobody uses too much of the liquidity



so i created a couple of interfaces that we're going to use to interact with all these contracts
first a simple interface for the Dai a stable coin then another interface for wrap ether
so on uni swap you cannot use ether directly but instead you use wrap ether.

the other important contract is the router that's the contract of uni swap that we are going to use
for trading and it has two important functions first get amounts out so it tell you how much token you're
gonna have as output for a certain number of tokens in input and also when you want to do your swap you are
going to call this function swap exact tokens for tokens so in argument you pass it the amount of token
in input so in our case it's going to be the amount for of wrap ether then you specify the minimum amount of
token that you're going to accept in output so in our case it's going to be the amount of Dai.
then an array of addresses to specify your trading path so in our case we're gonna trade
from wrap ether to die so the first address gonna be the address of wrap ether second address the address
of Dai then the recipient of the output token so in our case this is going to be the same address that sends the transaction and then the deadline so this is a timestamp in second that specify up to when the
transaction is valid so if you send transaction at a certain time you want amount out mint to be valid
only for stand time 

i created a scripts here to do the trading so let's go there so here we import the interface of the different smart contract we're going to interact with
then here we define the address of the different smart contract so for the router address you can find this in the documentation of uni swap for the address of wrap ether and die i found this on ether scan for
ring b.then amount in so that's the amount of wrap ether that we're going to provide in input so 0.1ether then we export a function so that's what's going to be executed
so first we get the address that's going to send the transaction then we create javascript object that points to our different smart contract then here we're going to deal with wrapether so the first line we're going to get some rap ether by sending some real ether then we're going to approve the router of uni swap to span our wrap ether then we're going to estimate how much dai toeknwe're going to get as output so that we use the router contract of unit swap
then we estimate how much ditokin we're going to get as output by using the router contract and the get the months out function so we pass it how much rap lifter we're going to provide in input and we also provide a trading path from
wrap ether to dai and then we're gonna get an array and we are interested in the second element of this array that's the amount of dai we're gonna get as output and with this value we're going to calculate amount out mean so this value
amounts at one that's valid at the time that we call get a month out but by the time we send our transaction maybe that we can get a slightly different number of token so we need to specify our tolerance and so here
our maximum tolerance is going to be ten percent less than amounts out or in other words amount out mean it's going to be ninetypercent of amount outs that we initially got so here since amounts out is an instance
of bnjs so that's a javascript library to deal with a big number the way we calculate ninety percent is a slightly more complex so that's why i use this two function here you cannot just directly
use the javascript operator to multiply by 90 and divide by 100 it will not work
then just after we get the balance of dai just before the transaction so that we can compare after then we finally do the trade here by using the swap exact tokens for tokens function
so we pass the amount of wrap ether and input the minimum amount of die in output then the trading pass then the recipient or transaction and then the deadline so this is a timestamp in second so i use a date.now of javascript that
gives us the current time step but in milliseconds
