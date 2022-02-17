<script>
    import {Styles, TabContent, TabPane} from "sveltestrap";
</script>
<Styles/>
<style>
    :global(#recordtab){
        margin-left: 15%;
        margin-top: 5%;
    }
</style>
<main class="page">
    <TabContent id="recordtab">
        <TabPane tabId="1" tab="1" active>
            <h2>1</h2>
        </TabPane>
        <TabPane tabId="2" tab="2" active>
            <h2>2</h2>
        </TabPane>
        <TabPane tabId="3" tab="3" active>
            <h2>3</h2>
        </TabPane>
        <TabPane tabId="4" tab="4" active>
            <h2>4</h2>
        </TabPane>
    </TabContent>


</main>
