<script>
import Router from 'svelte-spa-router'
import Navi from './components/Navi.svelte'
import index from './pages/index.svelte'
import test from  './pages/test.svelte'
import tasks from './pages/posts/index.svelte'
import tasks_show from './pages/posts/show.svelte'

export const routes = {
  '/': index,
  '/test': test,
  '/posts/': tasks,
  '/posts/show/:id': tasks_show,
}	
</script>

<!-- main -->
<main>
  <Navi />
  <Router {routes} />
</main>

<style>
  /*
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
  */
</style>