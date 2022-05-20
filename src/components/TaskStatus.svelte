<script>
    import "./scss/TaskStatus.scss";
    export let statusHandler;
</script>


<div class="status-dropdown">
    <input type="hidden"  />
    <ul class="nav dropdown">
        <li class="status-item status-dropdown-success" data-class="progress-status-success" on:click={ statusHandler }>Done</li>
        <li class="status-item status-dropdown-working" data-class="progress-status-working" on:click={ statusHandler } >Working on it</li>
        <li class="status-item status-dropdown-stuck"   data-class ="progress-status-stuck"  on:click={ statusHandler }>Stuck on it</li>
        <li class="status-item status-dropdown-prepare" data-class="progress-status-prepare" on:click={ statusHandler } >Prepare documentation</li>
    </ul>
</div>