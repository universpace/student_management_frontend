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
    let isClicked = false;
    let selectedStudent = null
    let categoryList = [
        {id:0,name:'학습'},
        {id:1,name:'생활'},
        {id:2,name:'인성'},
        {id:3,name:'특이사항'},
    ]
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
        isClicked = false
        let selectIndex = parseInt(e.target.parentElement.innerText[0])
        selectedStudent = foundStudentList[selectIndex]
        isClicked = true
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
    {#if isClicked && selectedStudent!==null}
    <Form on:submit={(e)=>e.preventDefault()}>
        <InputGroup>
            <Input type="select" name="selectCategory" id="selectCategory">
                <option disabled selected value> -- 선택해주세요 -- </option>
                {#each categoryList as ct}
                    <option value={ct}>{ct.name}<option>
                {/each}
            </Input>
        </InputGroup>
    </Form>
    {/if}
</main>
