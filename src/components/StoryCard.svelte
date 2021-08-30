<script>
	export let doc
  console.log(doc)

  const thumbnail = doc.multimedia.find(x => x.crop_name === "thumbStandard")
</script>

<a href={doc.web_url} target="_blank">
  {#if thumbnail}
    <img src="http://nytimes.com/{thumbnail.url}" />
  {/if}
  <h2>
    {doc.headline.main}
  </h2>
</a>


<style>
  a {
    color: inherit;
    display: block;
    text-decoration: none;
  }
  img {
    display: inline
  }
  h2 {
    display: inline;
  }
</style>
