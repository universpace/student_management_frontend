<script>
    import {Styles, Icon} from "sveltestrap";
    import {push} from 'svelte-spa-router'
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
    let student = [
        {
            menuName: '학생목록',
            url: '/#',
            iconName:'person-lines-fill'
        },
        {
            menuName: '학생등록',
            url: '/#',
            iconName:'person-plus-fill'
        }
    ]
    let record = [
        {
            menuName: '기록 목록',
            url: '/#/record',
            iconName:'person-lines-fill'
        },
        {
            menuName: '기록 등록',
            url: '/#/record',
            iconName:'person-plus-fill'
        }
    ]

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
    h3 {
        font-size: 1.5rem;
        /* margin-left:5% */
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
</style>
<aside class="sidebar">
    <menu>
        <li>

            <h3 class="student" on:click="{handleOnClick}">
                <Icon name="person-square"/>
                학생 관리
            </h3>
            {#if visibleStudent}
                {#each student as row}
                    <p class="student-menu"><a href="{row.url}" ><Icon name="{row.iconName}"/> {row.menuName}</a></p> 
                {/each}
            {/if}
        </li>
        <li>
            <h3 class="record" on:click="{handleOnClick}">
                <Icon name="file-text-fill"/>
                기록 관리
            </h3>
            {#if visibleRecord}
                {#each record as row}
                    <p class="record-menu"><a href="{row.url}"><Icon name="{row.iconName}"/> {row.menuName}</a></p> 
                {/each}
            {/if}
        </li>
    </menu>
</aside>