<script lang="ts">
    export let data: number[] = [];
    export let width = 400;
    export let height = 200;
    export let strokeColor = "blue";
    let max = Math.max(...data, 1);
    let points = data
        .map((value, index) => {
            let x = (index / (data.length - 1)) * width;
            let y = height - (value / max) * height;
            return `${x},${y}`;
        })
        .join(" ");
</script>

<svg
    {width}
    {height}
    viewBox={`0 0 ${width} ${height}`}
    style="border: 1px solid #ddd;"
>
    <polyline {points} fill="none" stroke={strokeColor} stroke-width="2" />
</svg>
