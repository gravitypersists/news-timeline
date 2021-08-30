<script>
  import dayjs from "dayjs"
  import { groupBy, range } from "ramda"
  import StoryCard from "./StoryCard.svelte"
	export let data

  const numDays = 30
  const day0 = dayjs("2017-1-20")
  const groupByDaysSinceDay0 = groupBy((doc) => {
    return dayjs(doc.pub_date).diff(day0, "days")
  })
  const docsByDays = groupByDaysSinceDay0(data)
</script>

{#each range(0, numDays) as day, i}
  <section>
    <div class="day-label">{day}</div>
    <div class="day-stories">
      {#each (docsByDays[day] || []) as doc, i}
        <StoryCard doc={doc} />
      {/each}
    </div>
  </section>
{/each}

<style>
  section {
    margin: 1px 0;
  }
  .day-label {
    height: 100px;
    color: #4ebeff;
    background-color: #f2faff;
    width: 26px;
    border: 1px solid;
    border-color: #4ebeff;
    border-radius: 4px;
    text-align: center;
    line-height: 100px;
  }
  .day-stories {

  }
</style>
