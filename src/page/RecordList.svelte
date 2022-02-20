<script>
    import {Form, FormGroup, Icon, Input, InputGroup, InputGroupText, Styles, TabContent, TabPane} from "sveltestrap";
    let student_name = null
    let status = 'learning';
</script>
<Styles/>
<style>
    :global(#recordtab){
        margin-left: 5%;

    }
    :global(#record-student-input){
        margin-left: 10%;
        margin-top: 4%;
    }
</style>
<main class="page">
    <Form id="record-student-input">
        <InputGroup>
            <Input placeholder="학생명" bsSize="bg" bind:value={student_name}/>
            <InputGroupText><Icon name="search"/></InputGroupText>
        </InputGroup>
    </Form>

    <TabContent id="recordtab" on:tab={(e) => (status = e.detail)}>
        <TabPane tabId="learning" tab="학습" active>

        </TabPane>
        <TabPane tabId="life" tab="생활">
            생활
        </TabPane>
        <TabPane tabId="tenacity" tab="인성">
            인성
        </TabPane>
        <TabPane tabId="remark" tab="특이사항">
            특이사항
        </TabPane>
    </TabContent>
</main>
