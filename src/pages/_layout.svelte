
<script>
    import Nav from '../components/NavBar.svelte';
    import Footer from '../components/Footer.svelte';
    import { onMount, onDestroy } from 'svelte';
    import  {callRemoteMenu} from '../remote/remo.svelte'; //funzione definita in navbar
    export let links;

   
     links =[
	['./index','homexxx','info',false, 'shop'],
	['./about','about','warning',true,'display'],
	['./login','login','success',true,'person-circle'],
	['./logout','logout','primary',true,'arrow-right-square'],
	['./blog','blog','danger',true,'globe']
];
    onMount(async () => {
      debugger
      console.log("linksa:",{links});
      callRemoteMenu('', setResult, setErr);// call rest
	});
   
    
    // setTimeout(function(){
    //   debugger;
      
    // }(3000));
    
    
    function setResult(data){
        console.log("setResult links : ",data.links);
          links=data.links;
        //  console.log(" links : ",links1);
    }
    function setErr(err){
      console.log("setErr : ",err);
    
    }
</script>
 
<Nav bind:links={links}/>
<slot></slot>
<Footer />