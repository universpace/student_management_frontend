<script>
    import {Button, Column, FormGroup, Input, Label, Styles, Table} from "sveltestrap";
    let studentList = [
      {
      "pk": 1,
      "name": "Conrado Emeny",
      "phoneNumber": "8893553049",
      "address": "Kingston",
      "addressDetail": "2 Muir Alley"
    }, {
      "pk": 2,
      "name": "Nicolina Persicke",
      "phoneNumber": "3086708979",
      "address": "Si Racha",
      "addressDetail": "45 Hallows Crossing"
    }, {
      "pk": 3,
      "name": "Dorrie Basillon",
      "phoneNumber": "2291071404",
      "address": "Tangkil",
      "addressDetail": "76 Lotheville Court"
    }, {
      "pk": 4,
      "name": "Web Lage",
      "phoneNumber": "7398733798",
      "address": "Kitāf",
      "addressDetail": "613 Mayfield Parkway"
    }, {
      "pk": 5,
      "name": "Collie Portinari",
      "phoneNumber": "7756711282",
      "address": "Plandi",
      "addressDetail": "7210 Debs Alley"
    }, {
      "pk": 6,
      "name": "Keriann Stuehmeier",
      "phoneNumber": "7166364008",
      "address": "Buffalo",
      "addressDetail": "24 Memorial Road"
    }, {
      "pk": 7,
      "name": "Carlee Clampton",
      "phoneNumber": "9924109441",
      "address": "Cuenca",
      "addressDetail": "09678 Redwing Plaza"
    }, {
      "pk": 8,
      "name": "Esteban Magnay",
      "phoneNumber": "5848368019",
      "address": "Shimabara",
      "addressDetail": "4 Crescent Oaks Way"
    }, {
      "pk": 9,
      "name": "Lowe McGown",
      "phoneNumber": "7545994893",
      "address": "Évreux",
      "addressDetail": "88 Milwaukee Place"
    }, {
      "pk": 10,
      "name": "Emmanuel Balleine",
      "phoneNumber": "8692382773",
      "address": "Baoquan",
      "addressDetail": "1 Mayer Plaza"
    }, {
      "pk": 11,
      "name": "April Hallmark",
      "phoneNumber": "7187861441",
      "address": "Pingshanhu",
      "addressDetail": "15696 Sunnyside Way"
    }, {
      "pk": 12,
      "name": "Mora Cockaday",
      "phoneNumber": "6284229005",
      "address": "Kedungcangkring",
      "addressDetail": "045 Kings Center"
    }, {
      "pk": 13,
      "name": "Matthew Ajean",
      "phoneNumber": "9151379454",
      "address": "Villaviciosa",
      "addressDetail": "72 Myrtle Terrace"
    }, {
      "pk": 14,
      "name": "Rodney Astell",
      "phoneNumber": "6305388326",
      "address": "Naperville",
      "addressDetail": "3 Springview Point"
    }, {
      "pk": 15,
      "name": "Dud Riach",
      "phoneNumber": "6593626350",
      "address": "Kuttu",
      "addressDetail": "221 Dorton Trail"
    }, {
      "pk": 16,
      "name": "Glenda Leijs",
      "phoneNumber": "8515669782",
      "address": "Tamnag",
      "addressDetail": "4271 East Hill"
    }, {
      "pk": 17,
      "name": "Morgan Hemmingway",
      "phoneNumber": "2925189653",
      "address": "Jönköping",
      "addressDetail": "925 Birchwood Avenue"
    }, {
      "pk": 18,
      "name": "Pace Tussaine",
      "phoneNumber": "2659386844",
      "address": "Markaz Bilād aţ Ţa‘ām",
      "addressDetail": "9 Dryden Street"
    }, {
      "pk": 19,
      "name": "Adriano Swains",
      "phoneNumber": "8231946433",
      "address": "Anyar",
      "addressDetail": "82126 John Wall Lane"
    }, {
      "pk": 20,
      "name": "Larisa Gurrado",
      "phoneNumber": "3042191639",
      "address": "Carcavelos",
      "addressDetail": "064 Sundown Junction"
    }, {
      "pk": 21,
      "name": "Skipp Lindenfeld",
      "phoneNumber": "7962502984",
      "address": "Lanyang",
      "addressDetail": "91199 Pawling Alley"
    }, {
      "pk": 22,
      "name": "Cloris Eskrigg",
      "phoneNumber": "6876595210",
      "address": "Thị Trấn Tà Lùng",
      "addressDetail": "43185 Mitchell Alley"
    }, {
      "pk": 23,
      "name": "Judi Flory",
      "phoneNumber": "9169081036",
      "address": "Kogon",
      "addressDetail": "0 Marcy Crossing"
    }, {
      "pk": 24,
      "name": "Slade Kenealy",
      "phoneNumber": "2075583590",
      "address": "Francisco Villa",
      "addressDetail": "79255 Merchant Parkway"
    }, {
      "pk": 25,
      "name": "Shea Livett",
      "phoneNumber": "1579928656",
      "address": "Itako",
      "addressDetail": "9 Independence Lane"
    }
  ]
    let picked = null
</script>
<Styles/>
<style>
    .tableContainer{
      margin-top: 10%; 
      margin-left:10%; 
      flex-direction: column; 
      width:40%;
      max-width:914px;
      height: 50%;
    }
    .tablebodyContainer{
        width: 100%;
        height: 100%;
        overflow:auto;
    }
    :global(#studentTable){
        width: 100%;
        background-color: white;
        height: 100%;
        /* max-height: 50%; */
        overflow:auto;
    }
    :global(#studentTableHead){
        
        width: 100%;
        max-width: 914px;
        background-color: white;
        /* max-height: 50%; */
        height: 5%;
        margin:0;
    }
    :global(#studentList){
        font-size:2em;
    }
    :global(#studentButton){
        margin-top: 5em;
        margin-right: 2em;
    }
</style>
<main class="page">
    <div class="tableContainer">
        <Table id="studentTableHead" bordered>
            <thead>
                <tr>
                    <td style="width:6.1%;"></td>
                    <td style="width:5.75%;">#</td>
                    <td style="width:26.6%;">이름</td>
                    <td style="width:16%;">전화번호</td>
                    <td>주소</td>
                </tr>
            </thead>
        </Table>
        <div class="tablebodyContainer">
            <Table id="studentTable" hover bordered>
                <tbody>
                    {#each studentList as {pk, name, phoneNumber, address, addressDetail},i}
                    <tr>
                        <td style="width:6.1%;"><Input id="{'student' +  pk}" bind:value={pk} type="radio" name="student" bind:group="{picked}"/></td>
                        <th style="width:5.75%;" scope="row">{pk}</th>
                        <td style="width:26.6%;">{name}</td>
                        <td style="width:16%;">{phoneNumber}</td>
                        <td>{address + ' ' + addressDetail}</td>
                    </tr>
                    {/each}
                </tbody>
            </Table>
        </div>
    </div>
    <div style="margin-left:5%; margin-top:20%;">
        {#if picked !== null}
            <p>학생이름 : {studentList[picked].name}</p>
            <p>전화번호 : {studentList[picked].phoneNumber}</p>
            <p>주　　소 : {studentList[picked].address + ' ' + studentList[picked].addressDetail}</p>
        {:else}
            <p style="visibility: hidden">text</p>
            <p style="visibility: hidden">text</p>
            <p style="visibility: hidden">text</p>
        {/if}
        <Button id="studentButton" color="primary" outline>수정하기</Button>
        <Button id="studentButton" color="danger">삭제하기</Button>
    </div>


</main>
