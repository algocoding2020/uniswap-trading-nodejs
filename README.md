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



