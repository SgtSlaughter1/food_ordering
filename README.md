
---

### **Project Assignment: Vue.js Food Ordering App**

#### **Objective:**
Create a simple food ordering app where users can view a list of available dishes, see details for each dish, and add items to an order cart.

#### **Instructions:**
1. **Bootstrap a Vue Project**:
   - Use Vue CLI to bootstrap a new Vue project from scratch.

2. **Core Features**:
   - **Dish List**: 
     - Display a list of dishes (e.g., image, name, price, description).
     - Use Vue's dynamic rendering (`v-for`) to loop through an array of dishes and display each one.
   
   - **Dish Details**:
     - When a user clicks on a dish, show additional details in a modal (use `Teleport` for rendering the modal outside the component).
   
   - **Add to Cart**:
     - Include an “Add to Cart” button for each dish. 
     - Use Vue methods to add items to the cart and display the cart summary (total items, total price).

3. **Additional Requirements**:
   - **Use Components**: 
     - Create separate components (e.g., `DishList`, `DishItem`, `CartSummary`) and pass data between them using props and events.
   
   - **Form Handling**: 
     - Include a form for the user to fill in delivery details (e.g., name, address) before placing an order.
     - Use `v-model` to bind form input values to the Vue component’s `data`.

   - **Watchers and Computed Properties**: 
     - Use a watcher to display a message when the cart has more than 5 items.
     - Use computed properties to calculate the total price dynamically.

   - **Conditional Rendering**: 
     - Show an "Order Successful" message conditionally after placing an order.

   - **Styling**:
     - Style the project using Bootstrap or plain CSS, ensuring it’s responsive and user-friendly.

#### **Stretch Goals (Optional)**:
   - **Search Functionality**: 
     - Implement a search bar to filter dishes by name or category.
   
   - **Category Filter**: 
     - Allow users to filter dishes by category (e.g., starters, mains, desserts).

---

### **Tools and Resources**:
- **Vue Documentation**: [Vue.js Docs](https://vuejs.org/)
- **W3Schools Vue Tutorials**: [W3Schools Vue.js Tutorials](https://www.w3schools.com/vue/)
- **Bootstrap for CSS**: [Bootstrap](https://getbootstrap.com/)

---
