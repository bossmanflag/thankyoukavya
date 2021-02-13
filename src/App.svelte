<script>
  import faunadb from "faunadb";
  const q = faunadb.query;
  const client = new faunadb.Client({
    secret: "fnAEB87W0AACAWYNCKLxsh75yc6Pc7YNOJUh6CdG",
  });
  let claps = 0;
  client
    .query(q.Get(q.Ref(q.Collection("claps"), "290427592526266881")))
    .then((ret) => {
      claps = ret.data.claps;
    });
  const clapUpdate = () => {
    client
      .query(q.Get(q.Ref(q.Collection("claps"), "290427592526266881")))
      .then((ret) => {
        console.log(ret.data.claps);
        client
          .query(
            q.Update(q.Ref(q.Collection("claps"), "290427592526266881"), {
              data: { claps: ret.data.claps + 1 },
            })
          )
          .then(() => {
            claps = ret.data.claps + 1;
          });
      });
  };
</script>

<main>
  <div class="heading">Thank you kavya</div>
  <div class="subtitle">
    This website is made for expressing how thankful i am to kavya. She is nice
    and all but she sent me maths assignment once and that helped me submit it
    to my nosy teacher. Kavya also has a lot of nice features as a friend
    really. She deserves clapping. Thank you best friend.
  </div>
  <div on:click={clapUpdate} class="button">Clap for kavya 👏</div>
  <div class="totalClaps">Total Clap kavya got: {claps}</div>
</main>

<style type="scss">
  main {
    text-align: center;
    padding: 1em;
    max-width: 50rem;
    border-radius: 3rem;
    display: flex;
    flex-direction: column;
    .heading {
      font-size: 5rem;
      padding: 1rem;
    }
    .subtitle {
      margin-top: 2rem;
      font-size: 1.2rem;
    }
    .button {
      padding: 1rem;
      background-color: bisque;
      max-width: 20rem;
      align-self: center;
      margin-top: 2rem;
      font-size: 1.5rem;
      font-weight: bold;
      border-radius: 1rem;
    }
    .totalClaps {
      font-weight: bold;
      font-size: 2rem;
      margin: 3rem;
    }
    .button:hover {
      background-color: rgb(233, 207, 175);
    }
    padding: 1rem;
    background-color: white;
  }
  :global(body) {
    background-color: #f1f1f1;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
</style>
