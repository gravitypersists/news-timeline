<script>
  import dayjs from "dayjs"
  import { groupBy, range } from "ramda"
  import VirtualList from '@sveltejs/svelte-virtual-list';
  import StoryCard from "./StoryCard.svelte"
	export let data

  const numDays = 365
  const day0 = dayjs("2017-1-20")
  const groupByDaysSinceDay0 = groupBy((doc) => {
    return dayjs(doc.pub_date).diff(day0, "days")
  })
  const docsByDays = groupByDaysSinceDay0(data)
  const dayNums = range(0, numDays)
</script>


<VirtualList items={dayNums} let:item>
  <section>
    <div class="day-label">{item}</div>
    <div class="day-stories">
      {#each (docsByDays[item] || []) as doc, i}
        <StoryCard doc={doc} />
      {/each}
    </div>
  </section>
</VirtualList>

<style>
  section {
    display: flex;
    align-items: flex-start;
    margin: 1px 0;
    height: 150px;
  }
  .day-label {
    align-self: stretch;
    color: #4ebeff;
    background-color: #f2faff;
    width: 26px;
    border: 1px solid;
    border-color: #4ebeff;
    border-radius: 4px;
    text-align: center;
    line-height: 150px;
    margin-right: 10px;
  }
  .day-stories {
    align-self: center;
  }
</style>
