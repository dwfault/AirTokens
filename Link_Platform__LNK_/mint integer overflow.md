### Link_Platform_\_LNK\_



https://etherscan.io/address/0xe2e6d4be086c6938b53b22144855eef674281639#code



```javascript
contract LinkToken is StandardToken, Ownable {

    string public   name =           "Link Platform";    // Name of the Token
    string public   symbol =         "LNK";              // ERC20 compliant Token code
    uint public     decimals =       18;                 // Token has 18 digit precision
    uint public     totalSupply;    			         // Total supply

    function mint(address _spender, uint _value)
        onlyOwner {

        balances[_spender] += _value;
        totalSupply += _value;
    }
}
```



The LNK token could be arbitrary minted by its creator in function mint(). The balances[_spender] and ) _value are a defined as uint, so oprator '+' would definitely result in an integer overflow.



Simulated on Remix:

![](./1.png)

The owner of the contract could mint arbitary amout of (for example 0x8000000000000000000000000000000000000000000000000000000000000000 Wei) subconcurrency LNK to an arbitary user.



![](./2.png)



If the owner of the contract mint another 0x8000000000000000000000000000000000000000000000000000000000000000 LNK to the user again,  integer overflow happened which make balanceOf this user to be 0.

And actually the owner of the contract could control the balance of an arbitary user to be an aribitary value. 



This is a serious problem for digital assets. Not a good thing for an organization who has a  poor code but fancy website(https://cryptolink.network).  





### Similar Vulnerabilities

##### SpadeICO
https://etherscan.io/address/0xfdb3c07c25f5a6879cc8b00685ed1a080c59615e#code

##### MoxyOnePresale 
https://etherscan.io/address/0x74fa9aa30b1b35c8f5bdb76f079c2624fc0b6498#code

##### GVToken Genesis Vision (GVT)
https://etherscan.io/address/0x103c3a209da59d3e7c4a89307e66521e081cfdf0#code

##### Etherty Token (ETY)
https://etherscan.io/address/0x0661f731f7f442a4147b87af5e77a9ecc7ed744e#code

##### Bitotal (TFUND)
https://etherscan.io/address/0xb334d6617dbe12fa75cc286436b7d20f8b04a4cb#code

##### SpadePreSale
https://etherscan.io/address/0x50ca2de80e803bf4b00f188545bca959540c5582#code

##### SP8DE PreSale Token (DSPX)
https://etherscan.io/address/0x30dda19c0b94a88ed8784868ec1e9375d9f0e27c#code

#####  ATLANT (ATL)
https://etherscan.io/address/0x78b7fada55a64dd895d8c8c35779dd8b67fa8a05#code
