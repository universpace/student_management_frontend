<script>
    import Sidebar from "./component/Sidebar.svelte";
    import StudentList from "./page/StudentList.svelte";
    import StudentReg from './page/StudentReg.svelte'
    import RecordList from './page/RecordList.svelte';
    import RecordReg from './page/RecordReg.svelte';
    import MainPage from "./page/MainPage.svelte";
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
    :global(.page){
        height: 100%;
        padding: 0;
        margin: 0;
        width: 100%;
        background-color:rgba(162, 232, 255, 0.548);
        display: flex;
    }
</style>
<main class="main_container">
    <div style="width:17%;max-width:230px">
        <Sidebar/>
    </div>
    <div style="width:100%">
        <Router routes={{
            '/':MainPage,
            '/student/list':StudentList,
            '/student/reg':StudentReg,
            '/record/list':RecordList,
            '/record/reg':RecordReg
            }
        }/>
    </div>
</main>

