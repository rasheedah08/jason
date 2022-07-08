<template>
  <table>
  <thead>
    <tr>
      <th>ID</th>
      <th>Image Preview</th>
      <th onclick="sortByTitle()">Title</th>
      <th onclick="sortByColor()">Color</th>
      <th>Image URL</th>
      <th><button id="addButton" onclick="toggleModal()"><i class="fa-solid fa-plus"></i></button></th>
    </tr>
  </thead>
  <tbody id="content">

  </tbody>
</table>

<div id="modal">
  <form onsubmit="event.preventDefault(); newProduct()">
    <h3>New Product <button style="aspect-ratio: 1; width: 40px" onclick="toggleModal()">X</button></h3>
    <input type="text" id="newTitle" placeholder="Title">
    <input type="text" id="newColor" placeholder="Color">
    <input type="text" id="newImage" placeholder="Image">
    <button type="submit">Add Product</button>
  </form>
</div>
</template>

<script>
export default {

}
</script>

<style>
img {
  width: 120px;
  aspect-ratio: 1;
  object-fit: cover;
}

table {
  width: 100%;
  border-spacing: 0;
  padding: 20px;
}

th {
  text-align: left;
}

th:hover {
  background: rgba(132, 94, 194, 0.1);
}
th button {
  width: 100%;
}

td,
th {
  overflow: hidden;
  padding: 5px;
}

table input {
  width: 100%;
  padding: 10px;
  background: #333;
  color: white;
  border: none;
  outline: none;
}

tr:nth-of-type(even) {
  background: rgba(132, 94, 194, 0.3);
}

tr:nth-of-type(even),
tr:nth-of-type(even) input,
tr:nth-of-type(even) input[disabled] {
  color: #666;
}

table input[disabled] {
  background: none;
  border: none;
  color: #333;
}
.options {
  display: flex;
  gap: 1%;
}
.options button {
  width: 50%;
}

button {
  background: #333;
  color: white;
  padding: 10px;
  border: none;
  outline: none;
}

#modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: cornflowerblue;
  padding: 20px;
  opacity: 0;
  z-index: -1;
  transition: all 0.3s linear;
}

#modal.active {
  opacity: 1;
  z-index: 10;
}

#modal h3 {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#modal form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

#modal form input {
  padding: 20px;
  background: none;
  color: #333;
  border: none;
  border-bottom: 2px solid #333;
}
#modal form input::placeholder {
  color: #333;
}
input {
  transition: all 0.3s linear;
}
input:focus {
  outline: none;
  border: none;
  background-color: rgba(0, 0, 0, 0.3) !important;
  color: white !important;
}
input:focus::placeholder {
  color: white !important;
}

@media screen and (max-width: 500px) {
  thead {
    position: fixed;
    left: -100vw;
  }
  tr {
    display: flex;
    flex-direction: column;
    padding: 20px;
    box-shadow: 1px 1px 6px rgba(0, 0, 0, 0.4);
    margin-bottom: 20px;
  }
  td {
    display: flex;
    align-items: center;
    font-size: 1rem;
    justify-content: space-between;
  }
  td:before {
    width: 40%;
    font-size: 1rem;
  }
  td:nth-child(1):before {
    content: "ID: ";
  }
  td:nth-child(2):before {
    content: "Image Preview: ";
  }
  td:nth-child(3):before {
    content: "Title: ";
  }
  td:nth-child(4):before {
    content: "Color: ";
  }
  td:nth-child(5):before {
    content: "Image URL: ";
  }

  td input {
    text-align: right;
    width: 60%;
  }

  #addButton {
    position: fixed;
    bottom: 5px;
    right: 5px;
    width: fit-content;
    display: grid;
    place-content: center;
    border-radius: 50%;
    padding: 20px;
    box-shadow: 1px 1px 6px rgba(0, 0, 0, 0.4);
  }
}

</style>