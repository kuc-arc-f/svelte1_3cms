<script>
import {link} from 'svelte-spa-router'
import marked from 'marked'
import LibCommon from '../../lib/LibCommon';
import LibCms from '../../lib/LibCms'

export let post = {};
export let params = Params
console.log(post)
//
async function get_items(){
  var dt = LibCommon.formatDate( new Date(), "YYYY-MM-DD_hhmmss");
  const res = await fetch(`/cms.json?` + dt  );
	const data = await res.json();
  var item  = LibCms.get_show_item( data.items, String(params.id) )
  item.content = marked(item.content)
  console.log(item)
  post =item
}
get_items() 
</script>

<!-- -->
<div class="container">
	<h1>{post.title}</h1>
  ID : {params.id}<br />
  Date : {post.created_at}
  <hr />
  <div id="post_item" >{@html post.content}
  </div>

</div>
