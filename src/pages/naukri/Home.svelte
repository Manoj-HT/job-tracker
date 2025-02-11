<script>
    import LineChart from "../../components/LineChart.svelte";
    let labels = ["Feb 1", "Feb 2", "Feb 3", "Feb 4", "Feb 5"];
    let searchAppearance = [10, 30, 30, 25, 35, 90];
    let appliedJobs = [5, 8, 15, 12, 20];
</script>

<div>Home</div>

<LineChart data={searchAppearance} strokeColor="red" width={500} height={500} />
