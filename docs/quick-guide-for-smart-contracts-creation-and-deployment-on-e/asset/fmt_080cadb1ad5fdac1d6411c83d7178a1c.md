
# SafeMath Library

Arithmetic operations in Solidity wrap on overflow. This can easily result in bugs, because programmers usually assume that an overflow raises an error, which is the standard behavior in high level programming languages. `SafeMath` restores this intuition by reverting the transaction when an operation overflows.

Using this library instead of the unchecked operations eliminates an entire class of bugs, so it's recommended to use it always.

```solidity
library SafeMath {

    /**
     * @dev Returns the addition of two unsigned integers, reverting on
     * overflow.
     *
     * Counterpart to Solidity's `+` operator.
     *
     * Requirements:
     * - Addition cannot overflow.
     */
    function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        require(c >= a, "SafeMath: addition overflow");
        return c;
    }

    /**
     * @dev Returns the subtraction of two unsigned integers, reverting on
     * overflow (when the result is negative).
     *
     * Counterpart to Solidity's `-` operator.
     *
     * Requirements:
     * - Subtraction cannot overflow.
     */
    function sub(uint256 a, uint256 b) internal pure returns (uint256) {
        return sub(a, b, "SafeMath: subtraction overflow");
    }

    /**
     * @dev Returns the subtraction of two unsigned integers, reverting with custom message on
     * overflow (when the result is negative).
     *
     * Counterpart to Solidity's `-` operator.
     *
     * Requirements:
     * - Subtraction cannot overflow.
     *
     * NOTE: This is a feature of the next version of OpenZeppelin Contracts.
     * @dev Get it via `npm install @openzeppelin/contracts@next`.
     */
    function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b <= a, errorMessage);
        uint256 c = a - b;
        return c;
    }

    /**
     * @dev Returns the multiplication of two unsigned integers, reverting on
     * overflow.
     *
     * Counterpart to Solidity's `*` operator.
     *
     * Requirements:
     * - Multiplication cannot overflow.
     */
    function mul(uint256 a, uint256 b) internal pure returns (uint256) {
        // Gas optimization: this is cheaper than requiring 'a' not being zero, but the
        // benefit is lost if 'b' is also tested.
        // See: https://github.com/OpenZeppelin/openzeppelin-contracts/pull/522
        if (a == 0) {
            return 0;
        }
        uint256 c = a * b;
        require(c / a == b, "SafeMath: multiplication overflow");
        return c;
    }

    /**
     * @dev Returns the integer division of two unsigned integers. Reverts on
     * division by zero. The result is rounded towards zero.
     *
     * Counterpart to Solidity's `/` operator. Note: this function uses a
     * `revert` opcode (which leaves remaining gas untouched) while Solidity
     * uses an invalid opcode to revert (consuming all remaining gas).
     *
     * Requirements:
     * - The divisor cannot be zero.
     */
    function div(uint256 a, uint256 b) internal pure returns (uint256) {
        return div(a, b, "SafeMath: division by zero");
    }

    /**
     * @dev Returns the integer division of two unsigned integers. Reverts with custom message on
     * division by zero. The result is rounded towards zero.
     *
     * Counterpart to Solidity's `/` operator. Note: this function uses a
     * `revert` opcode (which leaves remaining gas untouched) while Solidity
     * uses an invalid opcode to revert (consuming all remaining gas).
     *
     * Requirements:
     * - The divisor cannot be zero.
     * NOTE: This is a feature of the next version of OpenZeppelin Contracts.
     * @dev Get it via `npm install @openzeppelin/contracts@next`.
     */
    function div(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        // Solidity only automatically asserts when dividing by 0
        require(b > 0, errorMessage);
        uint256 c = a / b;
        // assert(a == b * c + a % b); // There is no case in which this doesn't hold
        return c;
    }

    /**
     * @dev Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),
     * Reverts when dividing by zero.
     *
     * Counterpart to Solidity's `%` operator. This function uses a `revert`
     * opcode (which leaves remaining gas untouched) while Solidity uses an
     * invalid opcode to revert (consuming all remaining gas).
     *
     * Requirements:
     * - The divisor cannot be zero.
     */
    function mod(uint256 a, uint256 b) internal pure returns (uint256) {
        return mod(a, b, "SafeMath: modulo by zero");
    }

    /**
     * @dev Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),
     * Reverts with custom message when dividing by zero.
     *
     * Counterpart to Solidity's `%` operator. This function uses a `revert`
     * opcode (which leaves remaining gas untouched) while Solidity uses an
     * invalid opcode to revert (consuming all remaining gas).
     *
     * Requirements:
     * - The divisor cannot be zero.
     *
     * NOTE: This is a feature of the next version of OpenZeppelin Contracts.
     * @dev Get it via `npm install @openzeppelin/contracts@next`.
     */
    function mod(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b != 0, errorMessage);
        return a % b;
    }
}
```

Then I called the library in `MyContract.sol` with import command. Now any arithmetic operation is easier. Here the `MyContract.sol` code:

```solidity
pragma solidity 0.5.1;

import "./SafeMath.sol";

contract MyContract {
    using SafeMath for uint256;

    uint256 public value;

    function calaculate (uint _value1, uint _value2) public {
        value = _value1.div(_value2);
    }
}
```

Attached screenshot when deploying `MyContract.sol`:

![](images/159551592354341205_10.jpg)

# 10. ERC-20 Smart Contract and Crowd Sale (ICO) Smart Contract

I'm going to show you how to code your own cryptocurrency on the Ethereum blockchain and sell it! I'll show you how to create your own ERC-20 token and crowd sale step-by-step with Ethereum smart contracts, how to test the smart contracts, how to deploy the smart contracts to the Ethereum blockchain, and how to build an ICO website deployed to the web. I'll also explain what an ERC-20 token is, how an Ethereum token works, how an initial coin offering (ICO) works.

## a. What is an ERC-20 Token?

The Ethereum blockchain allows you to create your own cryptocurrency, or token, that can be purchased with Ether, the native cryptocurrency of the Ethereum blockchain. ERC-20 is simply a standard that specifies how these tokens behave, so that they are compatible with other platforms like cryptocurrency exchanges.

Ethereum is a blockchain like Bitcoin. Like Bitcoin, Ethereum keeps track of account balances for people who own Ether, Ethereum's native cryptocurrency. Unlike Bitcoin, Ethereum is also a platform that allows you to create your own token without creating a new blockchain.

You can create an Ethereum token with a smart contract. ERC-20 is a standard that specifies how this token smart contract should work.

Let's use an example to understand how an ERC-20 token smart contract works. Let's say that we want to create a token called "My Token" with the symbol "MTK" and that there will be 100,000,000 of these tokens in existence.

First, the token smart contract keeps track of some basic token attributes. For example it records the name "My Token", the symbol that you see on a cryptocurrency exchange, and how many total tokens exist.

It also keeps track of who owns "My Token" and how much.

ERC-20 tokens can be transferred from one account to another as payment, just like any other cryptocurrency.

They can also be purchased in a crowd sale, like an ICO, which we will examine in the next section.

They can also be bought and sold on a cryptocurrency exchange.

## b. How ERC-20 Tokens Work
