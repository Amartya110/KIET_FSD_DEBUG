Solved Bugs
Bug 1: Price Range Filter Exclusion (App.js)
Symptom: Products at boundary prices (e.g., ₹500) were hidden.

Fix: Updated filter logic to use inclusive operators (>= and <=) instead of strict inequality.

Bug 2: Category Filter Inactive (App.js)
Symptom: Clicking category buttons didn't update the grid.

Fix: The category state variable is missing from the memo. 

Bug 3: Cart "Delete" Behavior (App.js)
Symptom: Deleting an item removed everything except that item.

Fix: Fixed the filter method logic. Changed (setCartItems(prev => prev.filter(i => i.id === id));) to (setCartItems(prev => prev.filter(i => i.id != id));) to correctly keep the items that were not selected for deletion.

Bug 4: Cart Badge Visibility (App.js)
Symptom: The header badge stayed at 0.

Fix:  change this to (const cartCount = cartItems.reduce((sum, i) => sum + i.count, 0);) to  (const cartCount = cartItems.reduce((sum, i) => sum + i.qty, 0);)

Bug 6: Cart Total Calculation (Cart.jsx)
Symptom: Total stayed at ₹0.

Fix: Same bug which is in 4 where count is written at place of qty, where count is not intialized.

Bug 7: Negative Quantity Prevention (Cart.jsx)
Symptom: Quantity could drop below 1.

Fix: Disabled attribute is already given, i have changed (disabled={item.qty <= 0}) to (disabled={item.qty <= 1},) so after qty 1 it will be disabled.

Bug 8: Inverted Sort Order (Filters.jsx)
Symptom: Low to High showed expensive items first.

Fix: In filter.jsx changed the code of 59 and 60, swapped the asc to desc.

Bug 9: Star Rating Rounding (ProductCard.jsx)
Symptom: 4.5 rating showed 4 stars.

Fix: Changed the loop condition from star <= Math.floor(rating) to star <= Math.ceil(rating) to include the partially filled star.

