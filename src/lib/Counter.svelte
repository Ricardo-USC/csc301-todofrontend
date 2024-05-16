<script>
  let data;

  async function apiCall() {
		const response = await fetch('https://csc301-todoserver-plum.vercel.app/todos');
		data = await response.json();
	}
  console.log(data);
</script>

<button on:click={apiCall}>
  count is {0} yay
</button>
