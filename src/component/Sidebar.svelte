<script>
    import {Styles, Icon} from "sveltestrap";
    import {slide} from 'svelte/transition'
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
            menuName: '학생 목록',
            url: '/#/student/list',
            iconName:'person-lines-fill'
        },
        {
            menuName: '학생 등록',
            url: '/#/student/reg',
            iconName:'person-plus-fill'
        }
    ]
    let record = [
        {
            menuName: '기록 목록',
            url: '/#/record/list',
            iconName:'person-lines-fill'
        },
        {
            menuName: '기록 등록',
            url: '/#/record/reg',
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
        cursor:pointer;
    }

    .student:hover, .record:hover {
        color: white;
    }

    .student-menu, .record-menu {
        margin-left: 22%;
    }
    h1 {
        margin-top: -30%;
        margin-bottom: 30%;
    }
</style>
<aside class="sidebar">
    <menu>
        <h1><a href="#"><Icon name="house-fill"/></a></h1>
        <li>
            <h3 class="student" on:click="{handleOnClick}">
                <Icon name="person-square"/>
                학생 관리
            </h3>
            {#if visibleStudent}
                {#each student as row}
                    <p class="student-menu" in:slide={{duration:1000}} out:slide={{duration:500}}><a href="{row.url}" ><Icon name="{row.iconName}"/> {row.menuName}</a></p>
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
                    <p class="record-menu" in:slide={{duration:1000}} out:slide={{duration:500}}><a href="{row.url}"><Icon name="{row.iconName}"/> {row.menuName}</a></p>
                {/each}
            {/if}
        </li>
    </menu>
</aside>