<script>
    import {Styles, Icon} from "sveltestrap";

    let visibleStudent = false;
    let visibleRecord = false;

    function handleOnClick(e) {
        let classList = e.target.classList
        if (classList[0] == 'student') {
            visibleRecord = false;
            visibleStudent = !visibleStudent;
        } else {
            visibleStudent = false;
            visibleRecord = !visibleRecord;
        }
    }
</script>
<Styles/>
<style>
    .sidebar {
        width: 100%;
        padding-top: 30%;
        background-color: cornflowerblue;
        height: 100%;
    }

    menu {
        margin: 0;

    }

    li {
        list-style: none;
        padding-left: 0;
        margin-bottom: 20%;
    }

    a {
        color: black;
        text-decoration: none;
        /*font-size: 1.5rem;*/
        /*font-weight: bold;*/
    }

    a:hover {
        color: white;
    }

    .student, .record {
        font-weight: bold;
    }

    .student:hover, .record:hover {
        color: white;
    }

    .student-menu, .record-menu {
        margin-left: 22%;
    }
    .activatemenu{
        color:white;
    }
</style>
<aside class="sidebar">
    <menu>
        <li>

            <h3 class="student" on:click="{handleOnClick}">
                <Icon name="person-square"/>
                학생 관리
            </h3>
            {#if visibleStudent}
                <p class="student-menu"><a href="#"><Icon name="person-lines-fill"/> 학생 목록</a></p>
                <p class="student-menu"><a href="#"><Icon name="person-plus-fill"/> 학생 등록</a></p>
            {/if}
        </li>
        <li>
            <h3 class="record" on:click="{handleOnClick}">
                <Icon name="file-text-fill"/>
                기록 관리
            </h3>
            {#if visibleRecord}
                <p class="record-menu"><a href="#"><Icon name="list-ul"/> 기록 목록</a></p>
                <p class="record-menu"><a href="#"><Icon name="file-plus"/> 기록 등록</a></p>
            {/if}
        </li>
    </menu>
</aside>