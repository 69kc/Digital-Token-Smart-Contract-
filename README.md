# Digital-Token-Smart-Contract-

pragma solidity ^0.8.0;

contract MyToken {
    string public name = "MyToken";
    string public symbol = "MT";
    uint256 public totalSupply = 1000000;
    mapping(address => uint256) public balances;

    constructor() {
        balances[msg.sender] = totalSupply;
    }

    function transfer(address _to, uint256 _amount) public returns (bool success) {
        require(balances[msg.sender] >= _amount);
        balances[msg.sender] -= _amount;
        balances[_to] += _amount;
        emit Transfer(msg.sender, _to, _amount);
        return true;
    }

    event Transfer(address indexed _from, address indexed _to, uint256 _amount);
}
