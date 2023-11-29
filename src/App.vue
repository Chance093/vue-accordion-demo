<script setup lang="ts"></script>

<template>
  <ul className="Accordion">
    <li className="Accordion_list Accordion_list_dropdown">
      <input
        type="checkbox"
        name="accordion"
        id="first"
        className="Accordion_input"
      />
      <label htmlFor="first" className="Accordion_label"> 11/23/2023 </label>
      <ul className="Accordion_content">
        <li className="Accordion_listItem">
          <p>Vendor Name</p>
          <p>Other Shit</p>
          <p>More Shit</p>
          <p>Even More Shit</p>
        </li>
      </ul>
    </li>
    <li className="Accordion_list Accordion_list_static">11/24/2023</li>
  </ul>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.Accordion {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 41.25rem;
}

.Accordion_list {
  list-style: none;
  border: 1px solid black;
  border-radius: 5px;
  transition: all 0.3s ease-in-out;
  padding: 1rem;
}

.Accordion_list_ .Accordion_list:hover {
  border: 1px solid rgb(105, 105, 105);
}

.Accordion_list_dropdown {
  background-color: rgb(104, 143, 104);
}

.Accordion_list_static {
  background-color: rgb(141, 52, 52);
  font-size: 1.4rem;
  padding-block: 1rem;
  text-align: left;
}

.Accordion_input {
  display: none;
}

.Accordion_label {
  display: flex;
  align-items: center;
  gap: 1rem;
  font-size: 1.4rem;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none;
}

.Accordion_content {
  line-height: 1.7rem;
  max-height: 0;
  overflow: hidden;
  padding-top: 0px;
  padding-inline: 1rem;
  transition: max-height 0.3s ease-in-out;
}

.Accordion_listItem {
  list-style: none;
  display: flex;
  justify-content: space-between;
}

.Accordion_input:checked + .Accordion_label + .Accordion_content {
  max-height: 400px;
}
</style>
