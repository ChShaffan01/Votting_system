// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

contract vottingsystem{

mapping (string => bool) names;
mapping (string => uint) candidates;
mapping (address => bool) validation;
mapping (address => bool) voters;

function addcandidates (string memory _name) public {
    require(validation[msg.sender] == false, "plz give me new id");
    candidates[_name] = 0;
    validation[msg.sender] = true;
    names[_name] = true;
}

function vote(uint _Age, string memory _name) public {
    require(names[_name] == true, "this candidate not recorded plz give me other candidate");
    require(voters[msg.sender] == false, "you already got a vote");
    require(_Age >= 18, "sorry but you are underage");
    candidates[_name]++;
    voters[msg.sender] = true;
}

function checkvote(string memory _name) public view returns (uint){
    return candidates[_name];
}


}
