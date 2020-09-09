<script>
  import { ajax } from "rxjs/ajax";
  import { pluck, startWith } from "rxjs/operators";

  export let name;

  const apiURL = "https://api.github.com/search/repositories?q=rxjs";

  const reposObservable = ajax(apiURL).pipe(
    pluck("response"),
    pluck("items"),
    startWith([])
  );
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h1>Hello {name}!</h1>
  <input type="text" bind:value={name} />
</main>
