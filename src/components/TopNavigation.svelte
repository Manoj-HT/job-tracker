<script></script>

<div class="container">
    <p>JOB TRACKER</p>
    <p>NAUKRI</p>
    <ul class="nav">
        <li class="nav_item">Home</li>
        <li class="nav_item">Add data</li>
    </ul>
</div>

<style>
    .container {
        width: 100%;
        height: 100%;
        border: 2px solid var(--theme);
        border-radius: 1rem;
        background-color: white;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 1rem;
    }
    .nav {
        list-style: none;
        display: flex;
        gap: 10px;
        height: 100%;
    }
    .nav_item {
        width: 100px;
        border-bottom: 5px solid transparent;
        border-top: 5px solid transparent;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: border-color var(--timing);
        cursor: pointer;
    }
    .nav_item:hover{
        border-bottom-color: var(--theme);
    }
</style>
