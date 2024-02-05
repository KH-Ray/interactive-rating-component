<script>
  import iconStar from "./assets/icon-star.svg";
  import thankYouImg from "./assets/illustration-thank-you.svg";

  let score = 0;
  let selectedBtn = null;
  let thankYouPage = false;

  function setScore({ target }) {
    score = Number(target.value);
    selectedBtn = target;
  }

  function setThankYouPage() {
    thankYouPage = true;
  }
</script>

<main class="main">
  <div class="box-placement">
    <div class="box">
      {#if !thankYouPage}
        <div class="first-row">
          <img src={iconStar} alt="Star Icon" class="star-icon" />
        </div>
        <div class="second-row">
          <h1>How did we do?</h1>
          <p>
            Please let us know how we did with your support request. All
            feedback is appreciated to help us improve our offering!
          </p>
        </div>
        <div class="third-row">
          <button
            on:click={setScore}
            class:button-active={Number(selectedBtn?.value) === 1}
            value={1}>1</button
          >
          <button
            on:click={setScore}
            class:button-active={Number(selectedBtn?.value) === 2}
            value={2}>2</button
          >
          <button
            on:click={setScore}
            class:button-active={Number(selectedBtn?.value) === 3}
            value={3}>3</button
          >
          <button
            on:click={setScore}
            class:button-active={Number(selectedBtn?.value) === 4}
            value={4}>4</button
          >
          <button
            on:click={setScore}
            class:button-active={Number(selectedBtn?.value) === 5}
            value={5}>5</button
          >
        </div>
        <div class="fourth-row">
          <button on:click={setThankYouPage} disabled={score === 0}
            >SUBMIT</button
          >
        </div>
      {:else}
        <div class="illustration-box">
          <img
            src={thankYouImg}
            alt="Thank you illustration"
            class="illustration"
          />
          <p class="score">You selected {score} of 5</p>
        </div>
        <div class="thank-you-msg-box">
          <p><strong>Thank you!</strong></p>
          <p class="thank-you-msg">
            We appreciate you taking the time to give a rating. If you ever need
            more support, don't hesitate to get in touch!
          </p>
        </div>
      {/if}
    </div>
  </div>
</main>

<style>
  .main {
    background-color: hsl(216, 12%, 8%);
  }

  .box-placement {
    max-height: 100%;
    min-height: 100vh;
    max-width: 38.4rem;
    margin: 0 auto;

    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 0.8rem;
  }

  .box {
    color: #fff;
    background: linear-gradient(hsl(213, 19%, 18%), hsl(210, 15%, 11%));
    padding: 2.4rem;
    border-radius: 1.2rem;
    width: 100%;
    height: 36rem;

    display: flex;
    justify-content: center;
    flex-direction: column;
    gap: 2.4rem;
  }

  /* First Page */
  .star-icon {
    padding: 1.2rem;
    height: 4rem;
    width: 4rem;
    border-radius: 100%;
    background-color: hsl(210, 20%, 24%);
  }

  .second-row {
    display: flex;
    flex-direction: column;
    gap: 0.8rem;
  }

  .second-row h1 {
    font-size: 2.4rem;
    font-weight: 700;
    line-height: 3.2rem;
  }

  .second-row p {
    font-size: 1.4rem;
    line-height: 2.2rem;
    color: hsl(216, 12%, 54%);
  }

  .third-row {
    display: flex;
    justify-content: space-between;
  }

  .third-row button {
    color: hsl(216, 12%, 54%);
    font-weight: 700;
    padding: 1.2rem;
    height: 4rem;
    width: 4rem;
    border: none;
    background-color: hsl(213, 19%, 18%);
    border-radius: 100%;
    cursor: pointer;
  }

  .third-row button:hover {
    background-color: hsl(25, 97%, 53%);
    color: hsl(0, 0%, 100%);
  }

  .fourth-row button {
    width: 100%;
    height: 4rem;
    border: none;
    border-radius: 9999px;
    cursor: pointer;
    background-color: hsl(25, 97%, 53%);
    color: hsl(0, 0%, 100%);
    font-weight: 700;
    letter-spacing: 0.1em;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  .fourth-row button:hover {
    background-color: hsl(0, 0%, 100%);
    color: hsl(25, 97%, 53%);
  }

  .fourth-row button:disabled {
    opacity: 50%;
    cursor: no-drop;
    background-color: hsl(25, 97%, 53%);
    color: hsl(0, 0%, 100%);
  }

  .button-active {
    background-color: hsl(0, 0%, 100%) !important;
    color: hsl(25, 97%, 53%) !important;
  }

  /* Second Page */
  .illustration-box {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 1.8rem;
  }

  .illustration {
    height: 9.6rem;
    widows: 9.6rem;
  }

  .score {
    display: flex;
    align-items: center;
    justify-content: center;

    font-size: 1.4rem;
    padding: 1rem 2rem;
    background-color: hsl(212, 20%, 18%);
    border-radius: 9999px;
    color: hsl(25, 97%, 53%);
    font-weight: 400;
    letter-spacing: 0.05em;
  }

  .thank-you-msg-box {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 1.2rem;
  }

  .thank-you-msg-box p strong {
    font-size: 2.4rem;
  }

  .thank-you-msg {
    text-align: center;
    font-size: 1.4rem;
    color: hsl(216, 12%, 54%);
  }
</style>
