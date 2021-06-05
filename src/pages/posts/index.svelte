<script>
import {link} from 'svelte-spa-router'
import Nav from '../../components/Navi.svelte';
import TopHeadBox from '../../components/TopHeadBox.svelte';
import IndexRow from './IndexRow.svelte';
import LibCommon from '../../lib/LibCommon';
import Config from '../../../app_config'
var config = Config.get_config()
export let cfg = config;
console.log(cfg)
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

<style>
.body_wrap{ position:relative; }
.badge_post{
  position:absolute; top:-15px; left:10px; 
}    
</style>
<!-- -->
<Nav />
<div class="body_main_wrap">
  <TopHeadBox site_name={config.MY_SITE_NAME} info_text={config.MY_SITE_INFO} />
  <div class="container">
    <div class="body_wrap card shadow-sm my-4">
      <span class="badge_post badge pt-2 pb-1 rounded myblog_bgcolor_accent px-3">
        <h5>Posts</h5>
      </span>
      <div id="post_items_box" class="card-body mt-2 mb-4">
        <div class="posts_items_row my-3">
          {#each posts as item}
          <IndexRow id={item.id} save_id={item.save_id} title={item.title} 
          date={item.created_at}  />        
          {/each}   
        </div>
      </div>
    </div>
    <h3>Posts - index</h3>
  </div>
</div>