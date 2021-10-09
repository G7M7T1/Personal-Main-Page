<script>
  let hours = 0;
  let minutes = 0;
  let seconds = 0;
  let HelloText = "";
  let searchInput = "";
  let newUrl = "";

  function Checktime() {
    const currentTime = new Date();
    hours = currentTime.getHours();
    minutes = currentTime.getMinutes();
    if (minutes < 10) {
      minutes = "0" + minutes;
    }
    seconds = currentTime.getSeconds();
    if (seconds < 10) {
      seconds = "0" + seconds;
    }
  }

  function CheckHelloText() {
    if (hours >= 5 && hours <= 10) {
      HelloText = "早上好";
    } else if (hours >= 11 && hours <= 14) {
      HelloText = "中午好";
    } else if (hours >= 15 && hours <= 18) {
      HelloText = "下午好";
    } else if (hours >= 19 && hours <= 23) {
      HelloText = "晚上好";
    } else if (hours >= 0 && hours <= 4) {
      HelloText = "凌晨咯";
    } else {
      HelloText = "检测中";
    }
  }
  setInterval(Checktime, 1000);
  setInterval(CheckHelloText, 1000);
  function CheckURL() {
    console.log(searchInput);
    searchInput = searchInput.replace(" ", "+");
    console.log(searchInput);
    newUrl = `https://www.google.ca/search?q=${searchInput}`;
    console.log(newUrl);
    window.open(newUrl, "_blank");
    searchInput = "";
  }
</script>

<main>
  <div class="bg">
    <div class="search">
      <input class="searchInput" bind:value={searchInput} type="text" />
      <button class="SearchBtn" on:click={CheckURL}>Search</button>
    </div>
    <h1 class="MainTitle">{`${hours}:${minutes}:${seconds}`}</h1>
    <h1 class="HelloText">{HelloText}</h1>
  </div>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Oswald&family=ZCOOL+KuaiLe&family=ZCOOL+QingKe+HuangYou&display=swap");

  :global(body) {
    background-image: url("/main.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    height: 100%;
    margin: 0;
    padding: 0;
  }

  .search {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin: 0rem;
    padding: 2rem;
  }

  .bg {
    background-color: rgba(0, 0, 0, 0.3);
    height: 100vh;
  }

  .searchInput {
    outline: none;
    background-color: rgba(0, 0, 0, 0.5);
    border: none;
    border-radius: 1rem;
    color: white;
    width: 20rem;
    padding: 0.6rem;
  }

  .SearchBtn {
    background-color: #ff3e00;
    border: none;
    border-radius: 1rem;
    position: relative;
    bottom: 45px;
    left: 125px;
    color: white;
  }

  .MainTitle {
    margin-top: 25rem;
  }

  main {
    text-align: center;
    margin: 0 auto;
  }

  .HelloText {
    font-size: 4em;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-family: "Oswald", sans-serif;
  }
</style>
