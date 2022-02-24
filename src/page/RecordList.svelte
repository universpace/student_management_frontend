<script>
    import {
        Alert,
        Button,
        Form,
        FormGroup,
        Icon,
        Input,
        InputGroup,
        InputGroupText, Modal, ModalBody, ModalFooter, ModalHeader,
        Styles,
        TabContent, Table,
        TabPane
    } from "sveltestrap";
    import { beforeUpdate, afterUpdate, tick} from 'svelte'
    let open = false;
    const toggle = () => {open = !open}
    let duplicate = false;
    let studentName = null
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
    let foundStudentList = []
    let selectedRecord = []
    let categoryList = [
        {id:0,name:'학습'},
        {id:1,name:'생활'},
        {id:2,name:'인성'},
        {id:3,name:'특이사항'},
    ]
    let newCategory = null
    function findStudent(element){
        return element.name === studentName;

    }
    function handleSearch(e){
        if(e.key==='Enter'){
            foundStudentList = studentList.filter(findStudent)
            selectedRecord = []
        }
        if(e.type==='click'){
            foundStudentList = studentList.filter(findStudent)
            selectedRecord = []
        }
    }
    function getStudentName(studentId){
        function findThisStudent(e){
            return e.id===studentId
        }
        return studentList.find(findThisStudent).name
    }
    function handleClick(e){
        let selectIndex = parseInt(e.target.parentElement.innerText[0])
        let selectedStudent = foundStudentList[selectIndex]
        function findRecord(e){
            return e.student===selectedStudent.id
        }
        selectedRecord = recordList.filter(findRecord)
        console.log(selectedRecord)
    }
    function addCategory(e){
        if(e.detail==="addCategory"){
            console.log(e)
            open = !open
        }
    }
    function createCategory(){
        if (newCategory !== null){
            let exlistCategory = categoryList.find(e=>e.name===newCategory)
            if(!exlistCategory){
                const category = {
                    id:categoryList.length,
                    name:newCategory
                }
                categoryList = [...categoryList, category]
            }
            else{
                duplicate = !duplicate
            }
        }
        open = !open
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
        display: flex;
        flex-direction: column;
    }
    :global(#duplicate-alert){
        position:absolute;
        margin-left: 28%;
        z-index: 100;
    }
</style>
<main class="page">
    <div id="record-student-input">
        <Form on:submit={(e)=>e.preventDefault()}>
            <InputGroup>
                <Input placeholder="학생명" bsSize="bg" bind:value={studentName} on:keydown={handleSearch}/>
                <InputGroupText><Button color="link" on:click={handleSearch}><Icon name="search"/></Button></InputGroupText>
            </InputGroup>
        </Form>
        <Table hover>
            {#each foundStudentList as student, index}
            <tr on:click="{handleClick}">
                <th scope="row">{index}</th>
                <td>{student.name}</td>
                <td>{student.phone_number}</td>
            </tr>
            {/each}
        </Table>
    </div>
    <TabContent id="recordtab" on:tab={addCategory}>
        {#each categoryList as category, idx}
            <TabPane tabId="{'tab'+category.id}" tab={category.name} active={idx===0}>
                {#each selectedRecord as record}
                    {#if record.category===category.name}
                        <p>학생명 : {getStudentName(record.student)}</p>
                        <p>내용 : {record.text}</p>
                    {/if}
                {/each}
            </TabPane>
        {/each}
        <TabPane tabId="addCategory" tab="+">
        </TabPane>
    </TabContent>
    <Modal isOpen={open} {toggle}>
        <ModalHeader {toggle}>새로운 카테고리 입력</ModalHeader>
        <ModalBody>
            새로운 카테고리를 생성해주세요
            <Input bind:value={newCategory} placeholdet="새로운 카테고리를 입력하세요"/>
        </ModalBody>
        <ModalFooter>
            <Button color="primary" on:click={createCategory}>생성</Button>
            <Button color="secondary" on:click={toggle}>닫기</Button>
        </ModalFooter>
    </Modal>
    <Alert color="primary" isOpen={duplicate} toggle={()=>duplicate = false} id="duplicate-alert" dismissible>
        카테고리는 중복으로 등록할 수 없습니다.
    </Alert>
</main>
