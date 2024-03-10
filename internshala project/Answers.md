[1].Explain the relationship between the "Product" and "Product_Category" entities from the above diagram.
answer:------>     ( The "Product" and "Product_Category" entities are related through the category_id field in the "Product" table.
In the diagram, the "Product_Category" entity has an 'N' (many) relationship with the "Product" entity, which has a '1' (one) relationship with the "Product_Category" entity. In other words, each product category can have multiple products associated with it, while each product can only belong to one category.
To clarify, the category_id field in the "Product" table is a foreign key referencing the id field in the "Product_Category" table. This means that for each product, there is a corresponding category_id that indicates which product category it belongs to.
One "Product_Category" can have many "Products."
Each "Product" belongs to only one "Product_Category.")



[2]. How could you ensure that each product in the "Product" table has a valid category assigned to it?

answer--------->    To ensure that each product in the "Product" table has a valid category assigned to it, we can enforce referential integrity by implementing a foreign key constraint on the category_id field in the "Product" table. This constraint would reference the id field in the "Product_Category" table.
When we create the foreign key constraint, you can specify that the category_id field should be NOT NULL, which means it cannot be left empty or set to NULL. This ensures that every product has a valid category assigned to it.
 example------>  ALTER TABLE product
ADD CONSTRAINT fk_product_category
FOREIGN KEY (category_id) REFERENCES product_category(id)
ON DELETE RESTRICT
ON UPDATE CASCADE
NOT NULL;
this SQL statement adds a foreign key constraint (fk_product_category) to the category_id field in the "Product" table, referencing the id field in the "Product_Category" table. The ON DELETE RESTRICT option prevents deletion of a category if there are still products associated with it, and the ON UPDATE CASCADE option updates the category_id in the "Product" table when the corresponding id is updated in the "Product_Category" table.

By enforcing the NOT NULL constraint, you ensure that each product in the "Product" table has a valid category assigned to it.