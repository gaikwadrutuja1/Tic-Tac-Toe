<!DOCTYPE html>
<html lang="en">
<head>
  <style>
      
*{
    margin: 0px;
    padding: 0px;
}
body{
    background-color: #548687;
    text-align: center;
}
.container{
    height: 70vh;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
}
.game{
    height: 60vmin;
    width: 60vmin;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 2vmin;

}
.box{
    height: 18vmin;
    width: 18vmin;
    border-radius: 1rem;
    border: none;
    box-shadow: 0 0 1rem rgba(0,0,0,0.3);
    font-size: 8vmin;
    color: #b0413e;
    background-color: rgb(200, 211, 160);
}
#resetbtn{
    padding : 1rem;
    font-size: 1.25rem;
    background-color: #191913;
    color:#fff;
    border-radius: 1rem;

}
#newbtn{
    padding : 1rem;
    font-size: 1.25rem;
    background-color: #191913;
    color:#fff;
    border-radius: 1rem;

}
#msg{
    color: #ffffc7;
    font-size: 8vmin;
}
.msg-container{
    height: 100vmin;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 4rem;
}
.hide{
    display: none;
}

  </style>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic -Tac -Toe</title>
</head>
<body>
    <div class ="msg-container hide">
        <p id ="msg">Winner</p>
    
        <button id ="newbtn">New Game</button>
    </div>
    <main>
    <h1>Tic - Tac - Toe</h1>
    <div class="container">
    <div class ="game">
        <button class ="box"></button>
        <button class ="box"></button>
        <button class ="box"></button>
        <button class ="box"></button>
        <button class ="box"></button>
        <button class ="box"></button>
        <button class ="box"></button>
        <button class ="box"></button>
        <button class ="box"></button>
    </div>
    </div>
    <button id ="resetbtn">Reset Game</button>
</main>
    <script>
        let boxes = document.querySelectorAll(".box");
let resetBtn = document.querySelector("#resetbtn");
let newGamebtn = document.querySelector("#newbtn");
let msgContainer = document.querySelector(".msg-container");
let msg = document.querySelector("#msg");
let turnO = true;//x,o
const winPaterrn =[
    [0,1,2],
    [3,4,5],
    [6,7,8],
    [0,3,6],
    [0,4,8],
    [1,4,7],
    [2,4,6],
    [2,5,8]
];
const resetGame = ()=>{
turnO =true;
enableboxes();
msgContainer.classList.add("hide");
};
boxes.forEach((box) => {
    box.addEventListener("click",() =>{
       // console.log("box was clicked");
        // box.innerText ="abcd";
        if(turnO){
           box.innerText = "O";
           turnO =false; 
        }
        else{
            box.innerText ="X";
            turnO =true;
        }
        box.disabled=true;
        checkWinner();
    });

});
const disableboxes = () =>{
    for(let box of boxes){
        box.disabled=true;
    }
}
const enableboxes = () =>{
    for(let box of boxes){
        box.disabled=false;
        box.innerText ="";
    }
}
const showWinner = (winner) =>{
msg.innerText = `Congrats winner is ${winner}`;
    msgContainer.classList.remove("hide");
}
const checkWinner =() =>{
    for(pattern of winPaterrn){
        // console.log([pattern[0]],[pattern[1]],[pattern[2]]);
        // console.log(
           let pos1Val  = boxes[pattern[0]].innerText;
           let pos2Val = boxes[pattern[1]].innerText;
           let pos3Val = boxes[pattern[2]].innerText;
           if(pos1Val!= "" && pos2Val!="" && pos3Val!=""){
            
            if(pos1Val==pos2Val && pos2Val==pos3Val)
{
    console.log("Winner",pos1Val);
    disableboxes();
    showWinner(pos1Val);
}
           }
    }

}
newGamebtn.addEventListener("click" , resetGame);
resetBtn.addEventListener("click",resetGame);
    </script>
</body>
</html>
