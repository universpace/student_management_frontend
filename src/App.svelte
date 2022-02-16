<script>
    import Sidebar from "./component/Sidebar.svelte";
    import {Col, Container, Row} from "sveltestrap";
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
    :global(#main){
        padding: 0;
        margin: 0;
        height: 100%;
    }
    :global(#column){
        padding: 0;
        height: 100%;
    }
</style>
<Container xxl id="main">
    <Row id="main">
        <Col sm="2" id="column">
            <Sidebar/>
        </Col>
        <Col id="column">

        </Col>
    </Row>
</Container>
