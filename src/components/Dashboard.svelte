<script>
     import { Container, Row, Col, TabPane, TabContent } from "sveltestrap";
     import IconButton, { Icon } from '@smui/icon-button';
     import { mdiReact, mdiGlasses, mdiPlus } from '@mdi/js';
     import { Svg } from '@smui/common/elements';
     import { onMount } from 'svelte';
     import "./scss/Dashboard.scss";
     import TaskStatus from "./TaskStatus.svelte";
     import FieldType from "./FieldType.svelte";
     import App from "../App.svelte";
    
     let nameArray;
      
     /* task Array sample Data */
     let taskArray = [{
	    projectname: "Production",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Three",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Three",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },
      {
	    projectname: "Staging Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Three",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },
      {
	    projectname: "Staging Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Three",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },
      {
	    projectname: "Staging Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Two",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Three",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Four",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Production Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Staging Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      },

      {
	    projectname: "Development Five",
        fieldList: ["Status", "Priority", "Research", "Assigned","Discussion","Next Meeting", "Need Development", "Assignee"],
        taskList: [
            {
                id: 1,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:2,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 3,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 4,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 5,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:6,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 7,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 8,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 9,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:10,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 11,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:12,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 13,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 14,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 15,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:16,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 17,
                taskName: 'Basics of Svelt',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 18,
                taskName: 'Welcome to Javascript',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id: 19,
                taskName: 'Welcome to HTML',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            },
            {
                id:20,
                taskName: 'Welcome to React',
                values:  { status: "Pending", priority: "High", research: "Analysis & Design", person: "Muhammad Bilal" , discussion: "April 23, 2022" , meeting: "Sep 30 2022" , assignee:"Kamran Shahid" }
            }
        ],
      }
    ];
     /* variables for state management */

        let currentColor = "#000";
        let isVisible = false;
        let showFieldType = false;
        let statusHandler;


        let statusValue =  [];

        let changeStatus = (e) => {
            let text = e.target.innerHTML;
            let className = e.target.getAttribute("data-class");
            let id = e.target.closest(".td-item").getAttribute("id");
            
            statusValue.push({
                id: id, 
                text : text,
                className: className,
            });
            console.log(statusValue);
        }
      
     /* show and hide Status */
      let show = false;
      const toggleStatus = (e) => {
        let children = e.target.closest(".td-item").children;
        children[1].classList.toggle("show"); 
      }

      /* toggle field type pop up */
      const toggleTypePopup = () => {
        showFieldType = !showFieldType;
      }

    /* toggleInput between div and input */
        const toggleInput = (e) => {
            if( e.target.name = "btn-edit") {
                let element  =  e.target.closest(".td-item");
                let children =  element.children;
                
                children[1].value = children[0].getAttribute("data-text");
                children[0].style.display = "none";
                children[1].style.display = "block";
                children[2].style.display = "none";
            }
        }

        /* hide input and show div */

        const hideInput = (e) => {
            let element  =  e.target.closest(".td-item");
            let children =  element.children;
            
            children[0].style.display = "block";
            children[1].style.display = "none";
            children[2].style.display = "none";
        }

        /* swap values between div and input */
        const changeValue = (e) => {
            console.log(e.target, "Design for input");
            let element  = e.target.closest(".td-item");
            let children =  element.children;
            children[0].setAttribute("data-text", children[1].value );
        }

</script>

<div class="main-dashboard">
    <Container>
        <section class="development-section">
            <h3 class="heading-main">Design and Development Task </h3>
            <p class="heading-bottom">Add Board Description</p>

            <div class="dashboard-table">
                <div class="dashboard-table-top">
                        <Row class="tabs-row">
                            <Col sm="12">
                                <div class="tabs-column">
                                    <TabContent>
                                        <TabPane tabId="mainTable" tab="Main Table" active>
                                            <div class="main-body">
                                                {#each taskArray  as task }
                                                    <div class="project-section">
                                                        <!-- Looping all values of Array -->
                                                        <div class="dashboard-row">
                                                            <div class="main-item prod-item">
                                                                <h3> <span>..</span> { task.projectname }</h3>
                                                            </div>

                                                            <div class="th-list">
                                                                {#each task.fieldList as field }
                                                                    <div class="th-item">{ field }</div>
                                                                {/each}
                                                                <div class="th-plus">
                                                                    <IconButton on:click = { (e) => { toggleTypePopup(e) }}>
                                                                        <Icon width={24} height={24} component={Svg} viewBox="0 0 24 24" class={ showFieldType ? "rotate-icon" : "" }>
                                                                            <path fill="{currentColor}" d={mdiPlus} />
                                                                        </Icon>
                                                                    </IconButton>

                                                                    { #if showFieldType }
                                                                        <FieldType />
                                                                    { /if }
                                                                </div>
                                                            </div>
                                                        </div>
                                                        {#each task.taskList as t, index }
                                                            <div class="dashboard-row content-row prod-row">
                                                                    <div class="td-item main-item">
                                                                        <div class="task-name" data-text="[WSK] 10 mins website video - T"> { t.taskName  }</div>
                                                                        <input type="text" name="task-name" class="form-control" on:change={ (e) => changeValue(e) } on:blur= { (e) => hideInput(e) }>
                                                                        <!-- <button class="btn btn-edit" name="btn-edit" on:click={ (e) => toggleInput(e) }>Edit</button> -->
                                                                    </div>
                                                                
                                                                    <div class="td-item">{ t.values.status }</div>
                                                                    <div class="td-item">{ t.values.priority} </div>
                                                                    <div class="td-item">{ t.values.research}</div>
                                                                    <div class="td-item user-item"><img src="images/user-image.png" alt="contributor" /></div>
                                                                    <div class="td-item">{ t.values.discussion }</div>
                                                                    <div class="td-item">{ t.values.meeting } </div>
                                                                    <div class={`td-item progress-status  ${ ( statusValue.id == index+1 ) ? statusValue.className : "" }`} id = {index + 1}  on:click={ e => toggleStatus(e) }> <span> { ( statusValue.id == index+1 ) ? statusValue.text : "Choose a value" } </span>
                                                                        <!-- show/hide Status -->
                                                                        <div class="show-status" class:show >
                                                                            <TaskStatus bind:statusHandler =  { changeStatus } />
                                                                        </div>
                                                                    </div>
                                                                    <div class="td-item user-item"><img src="images/user-image.png" alt="contributor" /></div>
                                                            </div>
                                                        {/each}      
                                                    </div>
                                                {/each}
                                                
                                            </div>
                                        </TabPane>
                                        <TabPane tabId="kanban" tab="Kanban">
                                            <p>Kanban Board</p>
                                        </TabPane>
                                    </TabContent>
                                </div>
                            </Col>
                        </Row>
                        
                        <div class="input-column">
                            <div class="input-group">
                                <input type="text" class="form-control" placeholder="Search">
                                <Icon class="material-icons">search</Icon>
                            </div>
                        </div>

                        <div class="button-column">
                            <div class="button-column-group">
                                <IconButton>
                                    <Icon width={24} height={24} component={Svg} viewBox="0 0 24 24">
                                        <path fill="{currentColor}" d={mdiReact} />
                                    </Icon>
                                </IconButton>
                                <IconButton>
                                    <Icon width={24} height={24} component={Svg} viewBox="0 0 24 24">
                                        <path fill="{currentColor}" d={ mdiGlasses } />
                                    </Icon>
                                </IconButton>
                            </div>
                        </div>
                </div>
            </div>


       </section>
    </Container>
    
</div>