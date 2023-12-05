<script setup lang="ts">
const sample = [
  {
    date: '11/30/2023',
    data: 'no entries as of timestamp',
    active: false,
    row: 1,
  },
  {
    date: '12/01/2023',
    data: [
      [
        'GL wholesale',
        'https://www.glwholesale.com/',
        'pzpurchasing@proglo.biz',
        'ProgloPurchase',
        'GL Wholesale _Nov 28 2023.xlsx',
        '-',
        true,
      ],
      [
        'Ultra DS / Ultra Standard Distributors',
        'https://www.ultradst.com/cgi/cgictl.pgm?PGMNAME:BSTHOM',
        'N/A',
        'N/A',
        'Ultra DS / Ultra Standard Distributors_Nov. 28 2023.xlsx',
        'Weekly they provide updated CSV file thru email',
        true,
      ],
      [
        'Aromar',
        'https://www.aromar.net/wholesale/',
        'pzpurchasing@proglo.biz',
        'ProgloPurchase',
        'Aromar_Nov. 28 2023.xlsx',
        '-',
        false,
      ],
    ],
    active: true,
    row: 2,
  },
  {
    date: '12/02/2023',
    data: 'no entries as of timestamp',
    active: false,
    row: 3,
  },
  {
    date: '12/03/2023',
    data: [
      [
        'Lev trading 2.0',
        'https://www.levtradingllc.com/',
        'N/A',
        'N/A',
        'Lev trading 2.0_Nov. 28 2023.xlsx',
        "most upc's is wrong - need to go over manually",
        true,
      ],
      [
        'EE SCHENCK',
        'https://eeschenck.com/',
        'N/A',
        'N/A',
        'EE SCHENCK_Nov. 28 2023.xlsx',
        '-',
        false,
      ],
      [
        'Brand Name Distributor ',
        'https://brandnamedistributors.com/',
        'N/A',
        'N/A',
        'BND _Nov 28 2023.xlsx',
        '-',
        false,
      ],
      [
        'Diamond Trading Group',
        '-',
        'mas@dtgny.us',
        '-',
        'DTG_Nov. 28 2023 .xlsx',
        '-',
        true,
      ],
    ],
    active: true,
    row: 4,
  },
];
</script>

<template>
  <ul class="Accordion">
    <template v-for="data in sample">
      <li v-if="data.active" class="Accordion_list Accordion_list_dropdown">
        <input
          v-if="data.active"
          type="checkbox"
          name="accordion"
          v-bind:id="data.row.toString()"
          class="Accordion_input"
        />
        <label v-bind:htmlFor="data.row.toString()" class="Accordion_label">
          {{ data.date }}
          <p>&#9660</p>
        </label>
        <div class="Accordion_content">
          <table v-if="data.active">
            <thead>
              <tr class="Accordion_tableRow Accordion_tableHead">
                <th class="Accordion_tableHeadItem">Vendor</th>
                <th class="Accordion_tableHeadItem">Website</th>
                <th class="Accordion_tableHeadItem">Email</th>
                <th class="Accordion_tableHeadItem">Password</th>
                <th class="Accordion_tableHeadItem Accordion_tableBodyCSV">
                  Recent CSV
                </th>
                <th class="Accordion_tableHeadItem">Notes</th>
                <th class="Accordion_tableHeadItem Accordion_tableBodyCheckbox">
                  Analysis Status
                </th>
              </tr>
            </thead>
            <tbody>
              <tr
                class="Accordion_tableRow Accordion_tableBody"
                v-for="item in data.data"
              >
                <td class="Accordion_tableBodyItem">{{ item[0] }}</td>
                <td class="Accordion_tableBodyItem">{{ item[1] }}</td>
                <td class="Accordion_tableBodyItem">{{ item[2] }}</td>
                <td class="Accordion_tableBodyItem">{{ item[3] }}</td>
                <td class="Accordion_tableBodyItem Accordion_tableBodyCSV">
                  <a v-bind:href="item[4]">Open</a>
                </td>
                <td class="Accordion_tableBodyItem">{{ item[5] }}</td>
                <td class="Accordion_tableBodyItem Accordion_tableBodyCheckbox">
                  <div class="checkbox-wrapper-18">
                    <div class="round">
                      <input
                        type="checkbox"
                        v-bind:id="'checkbox-' + item[1]"
                        v-bind:checked="item[6]"
                      />
                      <label v-bind:for="'checkbox-' + item[1]"></label>
                    </div>
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </li>
      <li v-else class="Accordion_list Accordion_list_static">
        {{ data.date }}
      </li>
    </template>
  </ul>
</template>

<style scoped>
.Accordion {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  color: black;
}

.Accordion_list {
  border-radius: 5px;
}

.Accordion_list_dropdown {
  background-color: #818cf8;
}

.Accordion_list_static {
  background-color: #94a3b8;
  font-size: 1.4rem;
  padding: 1rem;
  padding-inline: 2rem;
  text-align: left;
}

.Accordion_input {
  display: none;
}

.Accordion_label {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 1.4rem;
  cursor: pointer;
  padding: 1rem;
  padding-inline: 2rem;
  transition: all 0.3s ease-in-out;
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none;
}

.Accordion_label > p {
  font-size: 1rem;
}

.Accordion_content {
  max-height: 0;
  overflow: hidden;
  padding: 1rem;
  padding-block: 0;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  background-color: #c7d2fe;
  transition: max-height 0.3s ease-in-out;
  text-align: left;
}

table {
  table-layout: fixed;
  width: 100%;
}

a {
  background-color: #e0e7ff;
  padding: 0.5rem;
  padding-block: 0.2rem;
  border-radius: 5px;
  border: 2px solid #818cf8;
}

.Accordion_tableHeadItem {
  font-weight: 500;
  font-size: 1.1rem;
}

.Accordion_tableHeadItem,
.Accordion_tableBodyItem {
  padding: 1rem;
  overflow: hidden;
  overflow-wrap: break-word;
}

.Accordion_tableHead,
.Accordion_tableBody {
  border-bottom: 1px solid black;
}

.Accordion_tableBody:last-child {
  border-bottom: none;
}

.Accordion_tableBodyCheckbox,
.Accordion_tableBodyCSV {
  text-align: center;
}

.Accordion_input:checked + .Accordion_label + .Accordion_content {
  max-height: 3000px;
}

.checkbox-wrapper-18 .round {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.checkbox-wrapper-18 .round label {
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 50%;
  cursor: pointer;
  height: 28px;
  width: 28px;
  display: block;
  position: absolute;
}

.checkbox-wrapper-18 .round label:after {
  border: 2px solid #fff;
  border-top: none;
  border-right: none;
  content: '';
  height: 6px;
  left: 7px;
  opacity: 0;
  position: absolute;
  top: 9px;
  transform: rotate(-45deg);
  width: 12px;
}

.checkbox-wrapper-18 .round input[type='checkbox'] {
  visibility: hidden;
  display: none;
  opacity: 0;
}

.checkbox-wrapper-18 .round input[type='checkbox']:checked + label {
  background-color: #818cf8;
  border-color: #818cf8;
}

.checkbox-wrapper-18 .round input[type='checkbox']:checked + label:after {
  opacity: 1;
}
</style>
