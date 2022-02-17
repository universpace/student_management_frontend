<script>
    import {Button, Form, FormGroup, Input, Styles} from "sveltestrap";
    let name = ''
    let phoneNumber = ''
    function validateName(n){
        let patternName=/^[가-힣a-zA-Z]+$/
        return name.length > 0&&patternName.test(n)
    }
    function validatePhoneNumber(n){
        let patternPhone = /01[016789][^0][0-9]{2,3}[0-9]{3,4}/;
        return patternPhone.test(n)&&(n.length < 12)
    }
</script>
<Styles/>
<style>
    :global(#studentRegForm){
        margin-left: 25%;
        margin-top: 20%;
    }
</style>
<main class="page">
    <Form id="studentRegForm" >
        <FormGroup floating label="학생 이름">
            <Input placeholder="이름" bsSize="lg" bind:value={name}  invalid={!validateName(name)} valid={validateName(name)}/>
        </FormGroup>
        <FormGroup floating label="전화번호">
            <Input placeholder="-없이 입력해주세요" bind:value={phoneNumber}  invalid={!validatePhoneNumber(phoneNumber)} valid={validatePhoneNumber(phoneNumber)}/>
        </FormGroup>
        <FormGroup floating label="주소">
            <Input placeholder="서울특별시"/>
        </FormGroup>
        <FormGroup floating label="상세주소">
            <Input placeholder="101호"/>
        </FormGroup>
        <Button>등록하기</Button>
    </Form>
</main>
