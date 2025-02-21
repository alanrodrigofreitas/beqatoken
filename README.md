# Beqa Token (BEQA)

## Descrição
Beqa (BEQA) é um token ERC-20 desenvolvido com a biblioteca OpenZeppelin. Ele inclui funcionalidades avançadas como queima de tokens, permissões de assinatura (EIP-2612) e controle de propriedade para cunhagem segura.

## Recursos
- **ERC-20 Padrão**: Baseado em OpenZeppelin para segurança e compatibilidade.
- **Burnable**: Tokens podem ser queimados pelo detentor.
- **Ownable**: Apenas o dono do contrato pode cunhar novos tokens.
- **Permit (EIP-2612)**: Autoriza transações sem necessidade de aprovações on-chain.
- **Fornecimento Inicial**: 50.000.000 BEQA.

## Tecnologias Utilizadas
- Solidity ^0.8.22
- OpenZeppelin Contracts 5.0.0

## Implementação
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.22;

import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import {ERC20Burnable} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";
import {Ownable} from "@openzeppelin/contracts/access/Ownable.sol";

contract Beqa is ERC20, ERC20Burnable, Ownable, ERC20Permit {
    constructor(address initialOwner)
        ERC20("Beqa", "BEQA")
        Ownable(initialOwner)
        ERC20Permit("Beqa")
    {
        _mint(msg.sender, 50000000 * 10 ** decimals());
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }
}
```

## Como Usar
1. **Deploy**: Utilize Remix, Hardhat ou Truffle para implantar o contrato.
2. **Cunhar Tokens**: O proprietário pode cunhar novos BEQA com `mint(address to, uint256 amount)`.
3. **Queimar Tokens**: Qualquer detentor pode chamar `burn(uint256 amount)`.

## Licença
Distribuído sob a licença MIT.