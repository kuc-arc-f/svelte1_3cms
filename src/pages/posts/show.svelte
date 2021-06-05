<script>
import {link} from 'svelte-spa-router'
import Nav from '../../components/Navi.svelte';
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
<Nav />
<div class="container bg-light">
  <a href="/posts" class="btn btn-light btnx-outline-cyan mt-2" use:link>
    Back</a>
  <hr class="mt-2 mb-2" />
  <div class="show_head_wrap">
    <i class="bi bi-house-fill mx-2"></i> >
      &nbsp;{post.title}
  </div>
  <div class="card shadow-sm my-2">
    <div class="card-body">
      <h1>{post.title}</h1>
      Date: {post.created_at}<br />
      ID : {params.id}<br />
    </div>
  </div>    
  <div class="card shadow-sm mt-2 mb-4">
    <div class="card-body">
      <div id="post_item" >{@html post.content}
      </div>
    </div>
  </div>   

</div>
