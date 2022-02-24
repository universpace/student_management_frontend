<script>
    import {Button, Form, Icon, Input, InputGroup, InputGroupText, Styles, Table} from "sveltestrap";

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
    let foundStudentList = []
    function findStudent(element){
        return element.name === studentName;
    }
    function handleSearch(e){
        if(e.key==='Enter'){
            foundStudentList = studentList.filter(findStudent)
        }
        if(e.type==='click'){
            foundStudentList = studentList.filter(findStudent)
        }
    }
    function handleClick(e){
        let selectIndex = parseInt(e.target.parentElement.innerText[0])
        let selectedStudent = foundStudentList[selectIndex]
        function findRecord(e){
            return e.student===selectedStudent.id
        }
        // selectedRecord = recordList.filter(findRecord)
        // console.log(selectedRecord)
    }
</script>
<Styles/>
<style>
    :global(#record-student-input){
        margin-left: 10%;
        margin-top: 4%;
        display: flex;
        flex-direction: column;
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
</main>
