# Problem
You have a list of dishes. Each dish is associated with a list of ingredients used to prepare it. You want to group the dishes by ingredients, so that for each ingredient you'll be able to find all the dishes that contain it (if there are at least 2 such dishes).

Return an array where each element is a list with the first element equal to the name of the ingredient and all of the other elements equal to the names of dishes that contain this ingredient. The dishes inside each list should be sorted lexicographically. The result array should be sorted lexicographically by the names of the ingredients in its elements.

Example

For

    dishes = [  
              ["Salad", "Tomato", "Cucumber", "Salad", "Sauce"],  
              ["Pizza", "Tomato", "Sausage", "Sauce", "Dough"],  
              ["Quesadilla", "Chicken", "Cheese", "Sauce"],  
              ["Sandwich", "Salad", "Bread", "Tomato", "Cheese"]]  
            
the output should be

    groupingDishes(dishes) = [  
                              ["Cheese", "Quesadilla", "Sandwich"],  
                              ["Salad", "Salad", "Sandwich"],  
                              ["Sauce", "Pizza", "Quesadilla", "Salad"],  
                              ["Tomato", "Pizza", "Salad", "Sandwich"]]  
                            
For

    dishes = [  
              ["Pasta", "Tomato Sauce", "Onions", "Garlic"],  
              ["Chicken Curry", "Chicken", "Curry Sauce"],  
              ["Fried Rice", "Rice", "Onions", "Nuts"],  
              ["Salad", "Spinach", "Nuts"],  
              ["Sandwich", "Cheese", "Bread"],  
              ["Quesadilla", "Chicken", "Cheese"]]  
            
the output should be

    groupingDishes(dishes) = [  
                              ["Cheese", "Quesadilla", "Sandwich"],  
                              ["Chicken", "Chicken Curry", "Quesadilla"],  
                              ["Nuts", "Fried Rice", "Salad"],  

# Solution
```python
def groupingDishes(dishes):
    ret_dict = {}
    for i in dishes:
        for j in range(len(i)):
            if j == 0:
                pass
            else:
                if i[j] not in ret_dict:
                    ret_dict[i[j]] = [i[0]]
                else:
                    ret_dict[i[j]].append(i[0])
    
    length_keys = len(ret_dict)
    return_array = []
    
    for i in ret_dict:
        temp_array = []
        if (len(ret_dict[i]) >= 2):
            temp_array.append(i)
            temp_array.extend(ret_dict[i])
            return_array.append(temp_array)
            
    
    return_array.sort(key=lambda lst : lst[0])
    for i in range(len(return_array)):
        to_sort = return_array[i][1:]
        to_sort.sort()
        return_array[i][1:] = to_sort

    return return_array
```
                          
