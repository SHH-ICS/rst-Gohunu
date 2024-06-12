<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tic Tac Toe</title>
<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
    }
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
    .board {
        display: grid;
        grid-template-columns: repeat(3, 100px);
        grid-template-rows: repeat(3, 100px);
        grid-gap: 5px;
    }
    .cell {
        display: flex;
        justify-content: center;
        align-items: center;
        border: 1px solid #000;
        font-size: 2em;
        cursor: pointer;
    }
</style>
</head>
<body>
<div class="container">
    <div class="board" id="board">
        <div class="cell" onclick="handleClick(0)"></div>
        <div class="cell" onclick="handleClick(1)"></div>
        <div class="cell" onclick="handleClick(2)"></div>
        <div class="cell" onclick="handleClick(3)"></div>
        <div class="cell" onclick="handleClick(4)"></div>
        <div class="cell" onclick="handleClick(5)"></div>
        <div class="cell" onclick="handleClick(6)"></div>
        <div class="cell" onclick="handleClick(7)"></div>
        <div class="cell" onclick="handleClick(8)"></div>
    </div>
</div>

<script>
    let currentPlayer = 'X';
    let board = ['', '', '', '', '', '', '', '', ''];

    function handleClick(index) {
        if (!board[index]) {
            board[index] = currentPlayer;
            document.getElementById('board').children[index].innerText = currentPlayer;
            if (checkWinner(currentPlayer)) {
                alert(currentPlayer + ' wins!');
                resetBoard();
            } else if (board.every(cell => cell)) {
                alert('It\'s a draw!');
                resetBoard();
            } else {
                currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
            }
        }
    }

    function checkWinner(player) {
        const winConditions = [
            [0, 1, 2],
            [3, 4, 5],
            [6, 7, 8],
            [0, 3, 6],
            [1, 4, 7],
            [2, 5, 8],
            [0, 4, 8],
            [2, 4, 6]
        ];
        return winConditions.some(condition => condition.every(index => board[index] === player));
    }

    function resetBoard() {
        board = ['', '', '', '', '', '', '', '', ''];
        currentPlayer = 'X';
        document.querySelectorAll('.cell').forEach(cell => cell.innerText = '');
    }
</script>
</body>
</html>
