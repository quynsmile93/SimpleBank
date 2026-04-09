# SimpleBank
SimpleBank.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract SimpleBank {
    mapping(address => uint256) public balances;

    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }

    function withdraw(uint256 _amount) public {
        require(balances[msg.sender] >= _amount, "Not enough balance");
        balances[msg.sender] -= _amount;
        payable(msg.sender).transfer(_amount);
    }

    function getBalance() public view returns (uint256) {
        return balances[msg.sender];
    }
}
