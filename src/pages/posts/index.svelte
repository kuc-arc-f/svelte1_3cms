<script>
import {link} from 'svelte-spa-router'
import LibCommon from '../../lib/LibCommon';
export let posts = [];

async function get_items(){
  var dt = LibCommon.formatDate( new Date(), "YYYY-MM-DD_hhmmss");
  const res = await fetch(`/cms.json?` + dt  );
	const data = await res.json();
  var items =  LibCommon.get_reverse_items(data.items)
  posts =items
}
get_items() 
</script>

<!-- -->
<div class="container">
	<h3>Posts - index</h3>
  <hr />
  {#each posts as item}
  <h3><a href={`/posts/show/${item.save_id}`} use:link>{item.title}</a>
  </h3>
  <p>ID : {item.id}
  </p>  
  {/each}   
</div>
