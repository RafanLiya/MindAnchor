<script lang="ts">
  import { currentPage} from '../../lib/store';

  let name : string;
  type Schedule = {
    id: number;
    name: string,
    // startDate: string;
    // endDate: string;
    // startTime: string;
    // endTime: string;
  };

  // let startDate: string = '';
  // let endDate: string = '';
  // let startTime: string = '';
  // let endTime: string = '';

  function confirmSchedule(): void {
    // Check if all fields are filled
    // if (!startDate || !endDate || !startTime || !endTime) {
    //   alert("Please fill in all the date and time fields.");
    //   return;
    // }

    // // Combine date and time into Date objects for comparison
    // const start = new Date(`${startDate}T${startTime}`);
    // const end = new Date(`${endDate}T${endTime}`);

    // // Check if end date and time are before start date and time
    // if (end < start) {
    //   alert("The end date and time cannot be before the start date and time. And the name is optional");
    //   return;
    // }else if(start.getTime() === end.getTime() ){
    //   alert("The time cannot be the same!");
    //   return;
    // }
    // if(name == null){
    //   name = "untitled-"+localStorage.getItem('scheduleIdCounter');
    // }
    // scheduleIdCounter.update((currentId) => {
    //   const id = currentId; // Use current ID for the schedule
    //   const newId = currentId + 1; // Increment for the next schedule

    //   localStorage.setItem('scheduleIdCounter', newId.toString()); // Store updated ID
    //   return newId; // Update store value
    // });

    // Use the current ID value to create the schedule
    // scheduleIdCounter.subscribe((currentId) => {
    //   const schedule: Schedule = {
    //     id: currentId, // Use the updated ID here
    //     name,
        // startDate,
        // endDate,
        // startTime,
        // endTime,
      };

  //     scheduleStore.set(schedule);
  //     goToBackList_WhiteListPage();
  //     console.log("Activity Duration & To-Do List Confirmed:", schedule);
  //   });
  // }

  // function discardSchedule(): void {
  //   name = '';
  //   // startDate = '';
  //   // endDate = '';
  //   // startTime = '';
  //   // endTime = '';
  //   goToScheduleSummaryPage();
  // }

  function goToBackList_WhiteListPage() {
    currentPage.set('BlackList_WhiteListPage');
  }
  function goToScheduleSummaryPage(){
    currentPage.set('ScheduleSummaryPage');
  }
</script>

<div class="page1-container">
  <div class="page1-header">
    <img src="/icon.png" alt="MindAnchor Logo" width="25px" height="2px">
    <h1>MindAnchor</h1>
  </div>
  <hr />
  <!-- <div class="page1-duration">
    <label for="page1-duration" style="font-weight: bold;">Enter the duration of the activity:</label>
    <div id="page1-duration" class="page1-inputs">
      <input type="date" bind:value={startDate} placeholder="Start Date" name="Startdate" />
      <input type="date" bind:value={endDate} placeholder="End Date" name="EndDate" />
      <input type="time" bind:value={startTime} placeholder="Start Time" name="StartTime" />
      <input type="time" bind:value={endTime} placeholder="End Time" name="EndTime" />
    </div>
    <div style="display: flex;">
      <label for="Startdate" style="padding-right: 125px;font-weight:bold;">Start Date</label>
      <label for="Startdate" style="padding-right: 145px;font-weight:bold;">End Date</label>
      <label for="Startdate" style="padding-right: 130px;font-weight:bold;">Start Time</label>
      <label for="Startdate" style="font-weight:bold;">End Time</label>
    </div>
  </div> -->

  <div class="page1-tasks">
    <label for="page1-tasks" style="font-weight: bold;">Name this activity:</label>
    <div id="page1-tasks" class="page1-task-input">
      <input
        type="text"
        style="border-radius: 20px;"
        bind:value={name}
        placeholder="Enter a name for the schedule, or else it will be stored as untitled"
        on:keydown={(e) => e.key === 'Enter' && confirmSchedule()}
      />
    </div>
  </div>

  <div class="page1-actions">
    <button class="page1-confirm" on:click={confirmSchedule}>Confirm the name for this activity</button>
    <!-- <button class="page1-discard" on:click={discardSchedule}>Discard This Schedule</button> -->
  </div>
</div>
<style>
    :global(html, body) {
      margin: 0;
      padding: 0;
      overflow: hidden; /* Prevent scrolling */
      display: flex;
      justify-content: center;
      align-items: center;
      box-sizing: border-box;
      font-family: 'Inria Sans', sans-serif;
    }
    .page1-container {
      width: 984px;
      border: 1px solid #ccc;
      background-color: #fff;
      padding: 20px;
      box-sizing: border-box;
      overflow: hidden; /* Prevent internal scrolling */
      font-family: 'Inria Sans', sans-serif;
    }
  
    h1 {
      font-size: 1.8em;
      margin: 0 0 10px;
      font-weight: bold;
    }
  
    hr {
      border: 0;
      height: 2px;
      background-color: rgb(1, 1, 124);
      margin-bottom: 20px;
    }
  
    label {
      font-size: 1.2em;
      margin-bottom: 10px;
      display: block;
      color: #333;
    }
  
    /* .page1-duration,
    .page1-tasks {
      margin-bottom: 20px;
    } */
    /* .page1-inputs {
      display: flex;
      justify-content: space-between;
      gap: 10px;
    } */
  
    .page1-task-input {
      display: flex;
      gap: 10px;
      margin-top: 10px;
    }
  
    input {
      flex: 1;
      padding: 10px;
      font-size: 1em;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
  
    button {
      padding: 10px 15px;
      font-size: 1em;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
  
    button.page1-confirm {
      background-color: rgb(1, 1, 124);
      color: white;
    }
  
    button.page1-discard {
      background-color: red;
      color: white;
    }
    .page1-actions {
      display: flex;
      justify-content: space-between;
      margin-top: 20px;
    }
  
    .page1-header {
      display: flex;
      height: 25px;
      margin-bottom: 10px;
    }
    .page1-header h1 {
      font-size: 1.5em;
      margin-left: 10;
      margin-right: 400px;
    }
  
    .page1-header img {
      display: block;
    }
</style>