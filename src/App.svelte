<script>
    import Sidebar from "./component/Sidebar.svelte";
    import StudentManagement from "./page/Student_management.svelte";
    import RecordManagement from "./page/Record_management.svelte";
    import Router, {location, link} from 'svelte-spa-router';
</script>
<style>
    :global(body){
        padding: 0;
        height: 100%;
    }
    :global(html){
        padding: 0;
        height: 100%;
    }
    :global(#app){
        padding: 0;
        height: 100%;
    }

    .main_container{
        height: 100%;
        width:100%;
        display: flex;
    }
</style>
<main class="main_container">
    <div style="width:17%;max-width:230px">
        <Sidebar/>
    </div>
    <div style="width:100%">
        <Router routes={{
            '/':StudentManagement,
            '/record':RecordManagement
            }
        }/>
    </div>
</main>

