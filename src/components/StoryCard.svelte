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
    padding: 1px;
  }
  img {
    display: inline;
    height: 50px;
    width: 50px;
    vertical-align: bottom;
    border-radius: 5px;
  }
  h2 {
    display: inline;
    font-size: 20px;
    line-height: 50px;
    font-family: "serif"
  }
</style>
