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
<main2>
  <div class="heading">List of times kavya helped(true friend ❤️):<br /></div>

  <ol>
    <li>
      <div class="subtitle">
        I needed Verilog code for my exam the next day. I just needed code for 2
        chapters but she sent me code for all the chapters with all the DE
        records. Kavya is farfetch and a visionary. Thank you kavya (25FEB2021)
      </div>
    </li>
    <li>
      <div class="subtitle">
        Kavya is a caring and nice didi. This time i asked for a feed back about
        a small app that i build and she sat with me and gave me sexy sexy very
        nice feedback and told me that she was very proud of me :'). but she is
        also a little lazy so igave her little motivation now she is fine. that
        is what friends do for didi. now that it is established that she is
        didi, congratulations on defeating bjp. bad joke. Thank you kavya
        (4MAY2021)
      </div>
    </li>
  </ol>
</main2>

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
  main2 {
    text-align: center;
    padding: 1em;
    margin: 1em;
    max-width: 50rem;
    border-radius: 3rem;
    display: flex;
    flex-direction: column;
    .heading {
      font-size: 2rem;
      font-weight: bold;
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
