<script>
import { apiData, drinkNames } from './store.js';

  let count = 0
  const increment = () => {
    count += 1
  }

  const apiCall = ()=>
    fetch("https://csc301-todoserver-plum.vercel.app/todos")
  .then(response => response.json())
  .then(data => {
		console.log(data);
    apiData.set(data);
  }).catch(error => {
    console.log(error);
    return [];
  });
</script>

<button on:click={apiCall}>
  count is {count} yay
</button>
