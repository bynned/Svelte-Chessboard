<script>
  let size = 8;
  let board = Array.from({ length: size }).map((_, row) => 
    Array.from({ length: size }).map((_, col) => 
      (row + col) % 2 === 0 ? 'white' : 'black'
    )
  );

  function toggleColor(row, col) {
    board[row][col] = board[row][col] === 'white' ? 'black' : 'white';
  }
</script>

<style>
  .board {
    display: grid;
    grid-template-columns: repeat(8, 80px);
  	grid-template-rows: repeat(8, 80px);
  	width: 640px;
  	height: 640px;
  	border: 1px solid black;
  }

  .square {
    width: 80px;
    height: 80px;
  }

  .white {
    background-color: #fff;
  }

  .black {
    background-color: #000;
  }
</style>

<div class="board">
  {#each board as row, rowIndex}
    {#each row as square, colIndex}
      <div class="square {square}" on:click={() => toggleColor(rowIndex, colIndex)}></div>
    {/each}
  {/each}
</div>
