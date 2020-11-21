# **Token Ethereum**
Creación de un token ERC 20 en truffle

### Requerimientos
  - Truffle
  - Metamask
  - Node.js
  
### Pasos de ejecución
- Conectar metamask a la red de pruebas de goerli.
- En contracts/Token.sol edite el nombre y simbolo por el que se desea para su token.
```
pragma solidity 0.5.2;
import '@openzeppelin/contracts/token/ERC20/ERC20Mintable.sol';
contract Token is ERC20Mintable{
       string public name = "Pipe"; //aca
       string public symbol = "PIPE"; //aca
       uint8 public decimals = 2;
}

```
- Guarde su mnemonico de Metamask en .secret
- Compile el contrato inteligente desde la terminal con  **truffle compile**.
- Implementar en la red Goerli desde al terminal con **truffle migrate --network goerli**.

### Interacción con truffle desde la consola

- Conexion a la red goerli desde consola **truffle console --network goerli**
- Revisión de cuentas 
```
const accounts = await web3.eth.getAccounts()
Para mirar las cuentas
accounts
accounts[0]
accounts[1]
```
- Ver número del bloque
```
(await web3.eth.getBlockNumber()).toString()
```
- Emisión de tokens desde la consola

```
const token = await Token.deployed()


(await token.totalSupply()).toString()
accounts[0]
(await token.balanceOf(accounts[0])).toString()

#1000.00 tokens:
token.mint(accounts[0], 100000)

#agregar tokens a otra cuenta
token.mint("0x7ae691C61db6B167b8C83c9801B2Aa0D19698200", 100000)
```

### Verificar el Smart Contract Para que sea visible
```
npm install -D truffle-plugin-verify
https://github.com/rkalis/truffle-plugin-verify
Add the plugin to your truffle-config.js file
module.exports = {
  /* ... rest of truffle-config */

  plugins: [
    'truffle-plugin-verify'
  ]
  }

```






