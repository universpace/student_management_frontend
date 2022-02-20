<script>
    import {
        Button,
        Form,
        FormGroup,
        Icon,
        Input,
        InputGroup,
        InputGroupText,
        Styles,
        TabContent,
        TabPane
    } from "sveltestrap";
    let studentName = null
    let status = 'learning';
    let studentList = [
        {
            "id": 1,
            "name": "김우주",
            "phone_number": "01045342549",
            "address": "서울특별시 관악구 낙성대역길50",
            "address_detail": "102호"
        },
        {
            "id": 2,
            "name": "김갑철",
            "phone_number": "01011111111",
            "address": "인천광역시 중구 운서동",
            "address_detail": "7단지"
        },
        {
            "id": 4,
            "name": "김갑철",
            "phone_number": "01011111111",
            "address": "인천광역시 중구 운서동",
            "address_detail": "7단지"
        }
    ]
    let recordList = [
        {
            "id": 9,
            "student": 1,
            "category": "학습",
            "text": "12345",
            "hashtag": [
                "tag1",
                "tag2"
            ]
        },
        {
            "id": 8,
            "student": 1,
            "category": "생활",
            "text": "test",
            "hashtag": [
                "tag3",
                "tag4",
                "tag5"
            ]
        },
        {
            "id": 10,
            "student": 2,
            "category": "학습",
            "text": "갑테리몬",
            "hashtag": [
                "tag7",
                "tag8"
            ]
        }
    ]
    let foundStudent = null
    let selectedRecord = null

    function findStudent(element){
        if(element.name===studentName){
            return true
        }
        return false
    }
    function findRecord(element) {
        if (element.student === findStudent.id) {
            return true
        }
        return false
    }
    function handleSearch(e){
        console.log(e)
        if(e.key==='Enter'){
            foundStudent = studentList.find(findStudent)
            selectedRecord = recordList.find(findRecord)
        }
    }

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
            <Input placeholder="학생명" bsSize="bg" bind:value={studentName} on:keyup="{handleSearch}"/>
            <InputGroupText><Button color="link"><Icon name="search"/></Button></InputGroupText>
        </InputGroup>
    </Form>

    <TabContent id="recordtab" on:tab={(e) => (status = e.detail)}>
        <TabPane tabId="learning" tab="학습" active>
            {#if selectedRecord !== null}
                <p>{selectedRecord.text}</p>
            {:else}
                <p>1</p>
            {/if}
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
