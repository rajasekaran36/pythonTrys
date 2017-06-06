# Linear Searcher
[TOC]

## Problem Statement
Write a python program to do linear search operations on a list
0. Find the size of the list.
1. Is list is a MonoTypeList?
2. Is list is EmptyList?
3. Is list has only one Element?
4. Is Element is Available in the List?
5. Find Maximum Element in List.
6. Find Minimum Element in List.
7. Find Element at the position.
8. Find the position of the Element.
9. Find the List is Sorted or not.

## Solution Key
```python
def sizeOfList(list):
    return len(list)

def isMonoTypeList(list):
    type_to_compare = type(list[0])
    for thing in list:
        if type_to_compare != type(thing):
            return False
    return True

def isEmptyList(list):
    if sizeOfList(list) == 0:
        return True
    else:
        return False

def isSingleElementList(list):
    if sizeOfList(list) == 1:
        return True
    else:
        return False

def searcher(list, element):
    if isEmptyList(list):
       return "Empty List"
    else:
        for thing in list:
          if thing == element:
            return True
        return False   

def isAvailable(list, element):
    return searcher(list, element)

def findMaxElement(list):
    if not isEmptyList(list):
       if isSingleElementList(list):
          return list[0]
       else:
            max_element = list[0]
            for element in list:
                if(max_element <= element):
                  max_element = element
            return max_element
    else:
        return "Invalid List"

def findMinElement(list):
    if not isEmptyList(list):
       if isSingleElementList(list):
          return list[0]
       else:
            min_element = list[0]
            for element in list:
                if(min_element >= element):
                  min_element = element
            return min_element
    else:
        return "Invalid List"

def findFirstElement(list):
    if not isEmptyList(list):
       if isSingleElementList(list):
          return list[0]
       else:
            return list[0]
    else:
        return "Invalid List"

def findLastElement(list):
    if not isEmptyList(list):
       if isSingleElementList(list):
          return list[0]
       else:
            return list[sizeOfList(list)-1]
    else:
        return "Invalid List"

def findPositionOfElement(list, element_to_find_position):
    if not isEmptyList(list)  and isAvailable(list, element_to_find_position):
       if isSingleElementList(list):
          return 0
       else:
            position = 0
            for element in list:
                if element == element_to_find_position:
                   return position
                else:
                   position += 1
    else:
        return "Can't Find an Element in List"

def isSortedList(list):
    if not isEmptyList(list) and isMonoTypeList(list):
       if isSingleElementList(list):
          return True
       else:
            first_element = findFirstElement(list)
            last_element = findLastElement(list)
            if first_element < last_element:
               for element in list:
                   if element < first_element or element > last_element:
                      return False
               return True
            else:
                 if first_element > last_element:
                    for element in list:
                       if element > first_element or element < last_element:
                          return False
                    return True
    else:
        return "Invalid List"

def findTheElementInPosition(list, position_of_element):
    if (not isEmptyList(list)):
       if ((sizeOfList(list)-1) >= position_of_element):
           return list[position_of_element]
       else:
           return "Position is OutBound"
    else:
        return "Invalid List"
```
## Test Cases 

```python
import LinearSearcher
import unittest

class TestLinearSearcher(unittest.TestCase):

#Test 1
    def test_list_element_is_available(self):
        '''find the element 5 in list'''
        list = [3, 1, 5, 2, 4]
        expected = True
        actual = LinearSearcher.isAvailable(list, 5)
        self.assertEqual(expected, actual)    

#Test 2
    def test_list_element_is_not_available(self):
        '''find the element 5 in list'''
        list = [3, 1, 5, 2, 4]
        expected = False
        actual = LinearSearcher.isAvailable(list, 6)
        self.assertEqual(expected, actual)

#Test 3
    def test_list_list_is_mono_type_true(self):
        '''Expected list is mono type'''
        list = [3, 1, 5, 2, 4]
        expected = True
        actual = LinearSearcher.isMonoTypeList(list)
        self.assertEqual(expected, actual)

#Test 4
    def test_list_list_is_mono_type_false(self):
        '''Expected list is non mono type'''
        list = [3, 1, 5, 2, 4, "Six"]
        expected = False
        actual = LinearSearcher.isMonoTypeList(list)
        self.assertEqual(expected, actual)

#Test 5    
    def test_list_list_is_empty(self):
        '''Expected list is Empty'''
        list = []
        expected = True
        actual = LinearSearcher.isEmptyList(list)
        self.assertEqual(expected, actual)

#Test 6   
    def test_list_list_is_non_empty(self):
        '''Expected list is Non_Empty'''
        list = [1]
        expected = False
        actual = LinearSearcher.isEmptyList(list)
        self.assertEqual(expected, actual)

#Test 7
    def test_list_find_size_of_list(self):
        '''Expected Size is 5'''
        list = [3, 1, 5, 2, 4]
        expected = 5
        actual = LinearSearcher.sizeOfList(list)
        self.assertEqual(expected, actual)

#Test 8    
    def test_list_for_single_element(self):
        '''Expected isSilgleElementList is True'''
        list = [3]
        expected = True
        actual = LinearSearcher.isSingleElementList(list)
        self.assertEqual(expected, actual)

#Test 9   
    def test_list_search_for_element_in_empty_list(self):
        '''Searching for element 3 in empty list'''
        list = []
        expected = "Empty List"
        actual = LinearSearcher.searcher(list,3)
        self.assertEqual(expected, actual)

#Test 10    
    def test_list_finding_max_element_in_list(self):
        '''List has max element is 10'''
        list = [1, 2, 3, 10, 4, 7, 5, 9, 0]
        expected = 10
        actual = LinearSearcher.findMaxElement(list)
        self.assertEqual(expected, actual)

#Test 11    
    def test_list_finding_max_element_in_list_empty_list(self):
        '''Empty list but we trying to find element 10'''
        list = []
        expected = "Invalid List"
        actual = LinearSearcher.findMaxElement(list)
        self.assertEqual(expected, actual)

#Test 12    
    def test_list_finding_min_element_in_list(self):
        '''List has max element is 10'''
        list = [1, 2, 3, 10, 4, 7, 5, 9, 0]
        expected = 0
        actual = LinearSearcher.findMinElement(list)
        self.assertEqual(expected, actual)
#Test 13    
    def test_list_finding_min_element_in_list_empty_list(self):
        '''Empty list but we trying to find element 10'''
        list = []
        expected = "Invalid List"
        actual = LinearSearcher.findMinElement(list)
        self.assertEqual(expected, actual)

#Test 14    
    def test_list_finding_first_element_in_list(self):
        '''List has first element is 1'''
        list = [1, 2, 3, 10, 4, 7, 5, 9, 0]
        expected = 1
        actual = LinearSearcher.findFirstElement(list)
        self.assertEqual(expected, actual)

#Test 15    
    def test_list_finding_first_element_in_list_empty_list(self):
        '''Empty list but we trying to find first element'''
        list = []
        expected = "Invalid List"
        actual = LinearSearcher.findFirstElement(list)
        self.assertEqual(expected, actual)

#Test 16    
    def test_list_finding_last_element_in_list(self):
        '''List has last element is 1'''
        list = [1, 2, 3, 10, 4, 7, 5, 9, 20]
        expected = 20
        actual = LinearSearcher.findLastElement(list)
        self.assertEqual(expected, actual)

#Test 17    
    def test_list_finding_last_element_in_list_empty_list(self):
        '''Empty list but we trying to find last element'''
        list = []
        expected = "Invalid List"
        actual = LinearSearcher.findLastElement(list)
        self.assertEqual(expected, actual)

#Test 18
    def test_list_finding_position_of_element_in_list(self):
        '''List has last element is 1'''
        list = [1, 2, 3, 10, 4, 7, 5, 9, 20]
        expected = 3
        actual = LinearSearcher.findPositionOfElement(list,10)
        self.assertEqual(expected, actual)

#Test 19
    def test_list_finding_position_of_element_not_available_in_list(self):
        '''List has last element is 1'''
        list = [1, 2, 3, 10, 4, 7, 5, 9, 20]
        expected = "Can't Find an Element in List"
        actual = LinearSearcher.findPositionOfElement(list,50)
        self.assertEqual(expected, actual)

#Test 20
    def test_list_finding_the_list_is_sorted_in_assending_order(self):
        '''This is Sorted List'''
        list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
        expected = True
        actual = LinearSearcher.isSortedList(list)
        self.assertEqual(expected, actual)

#Test 21
    def test_list_finding_the_list_is_sorted_in_desending_order(self):
        '''This is Sorted List'''
        list = [9, 8, 7, 6, 5, 4, 3, 2, 1]
        expected = True
        actual = LinearSearcher.isSortedList(list)
        self.assertEqual(expected, actual)

#Test 22
    def test_list_finding_the_list_is_not_sorted(self):
        '''This is Non Sorted List'''
        list = [1, 7, 3, 4, 9, 6, 2, 8, 5]
        expected = False
        actual = LinearSearcher.isSortedList(list)
        self.assertEqual(expected, actual)

#Test 23
    def test_list_finding_the_list_is_sorted_but_list_is_empty(self):
        '''This is Non Sorted List'''
        list = []
        expected = "Invalid List"
        actual = LinearSearcher.isSortedList(list)
        self.assertEqual(expected, actual)

#Test 24
    def test_list_finding_the_element_in_position_of_list(self):
        '''List has Element 7 in 5th position'''
        list = [1, 10, 3, 4, 9, 7, 2, 8, 10]
        expected = 7
        actual = LinearSearcher.findTheElementInPosition(list, 5)
        self.assertEqual(expected, actual)

#Test 25
    def test_list_finding_the_element_in_position_of_list_position_outbound(self):
        '''List has Element 7 in 5th position'''
        list = [1, 10, 3, 4, 9, 7, 2, 8, 10]
        expected = "Position is OutBound"
        actual = LinearSearcher.findTheElementInPosition(list, 20)
        self.assertEqual(expected, actual)

#Test 26
    def test_list_finding_the_element_in_position_of_list_but_list_is_empty(self):
        '''Empty List but tyring to find element in 5th position'''
        list = []
        expected = "Invalid List"
        actual = LinearSearcher.findTheElementInPosition(list, 5)
        self.assertEqual(expected, actual)
if __name__ == '__main__':
    unittest.main()

```
## PythonTutor Visualizer
http://pythontutor.com/visualize.html#code=def%20sizeOfList%28list%29%3A%0A%20%20%20%20return%20len%28list%29%0A%0Adef%20isMonoTypeList%28list%29%3A%0A%20%20%20%20type_to_compare%20%3D%20type%28list%5B0%5D%29%0A%20%20%20%20for%20thing%20in%20list%3A%0A%20%20%20%20%20%20%20%20if%20type_to_compare%20!%3D%20type%28thing%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20False%0A%20%20%20%20return%20True%0A%0Adef%20isEmptyList%28list%29%3A%0A%20%20%20%20if%20sizeOfList%28list%29%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20return%20True%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20False%0A%0Adef%20isSingleElementList%28list%29%3A%0A%20%20%20%20if%20sizeOfList%28list%29%20%3D%3D%201%3A%0A%20%20%20%20%20%20%20%20return%20True%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20False%0A%0Adef%20searcher%28list,%20element%29%3A%0A%20%20%20%20if%20isEmptyList%28list%29%3A%0A%20%20%20%20%20%20%20return%20%22Empty%20List%22%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20for%20thing%20in%20list%3A%0A%20%20%20%20%20%20%20%20%20%20if%20thing%20%3D%3D%20element%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20True%0A%20%20%20%20%20%20%20%20return%20False%20%20%20%0A%0Adef%20isAvailable%28list,%20element%29%3A%0A%20%20%20%20return%20searcher%28list,%20element%29%0A%0Adef%20findMaxElement%28list%29%3A%0A%20%20%20%20if%20not%20isEmptyList%28list%29%3A%0A%20%20%20%20%20%20%20if%20isSingleElementList%28list%29%3A%0A%20%20%20%20%20%20%20%20%20%20return%20list%5B0%5D%0A%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20max_element%20%3D%20list%5B0%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20element%20in%20list%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%28max_element%20%3C%3D%20element%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20max_element%20%3D%20element%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20max_element%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20%22Invalid%20List%22%0A%0Adef%20findMinElement%28list%29%3A%0A%20%20%20%20if%20not%20isEmptyList%28list%29%3A%0A%20%20%20%20%20%20%20if%20isSingleElementList%28list%29%3A%0A%20%20%20%20%20%20%20%20%20%20return%20list%5B0%5D%0A%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20min_element%20%3D%20list%5B0%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20element%20in%20list%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%28min_element%20%3E%3D%20element%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20min_element%20%3D%20element%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20min_element%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20%22Invalid%20List%22%0A%0Adef%20findFirstElement%28list%29%3A%0A%20%20%20%20if%20not%20isEmptyList%28list%29%3A%0A%20%20%20%20%20%20%20if%20isSingleElementList%28list%29%3A%0A%20%20%20%20%20%20%20%20%20%20return%20list%5B0%5D%0A%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20list%5B0%5D%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20%22Invalid%20List%22%0A%0Adef%20findLastElement%28list%29%3A%0A%20%20%20%20if%20not%20isEmptyList%28list%29%3A%0A%20%20%20%20%20%20%20if%20isSingleElementList%28list%29%3A%0A%20%20%20%20%20%20%20%20%20%20return%20list%5B0%5D%0A%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20list%5BsizeOfList%28list%29-1%5D%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20%22Invalid%20List%22%0A%0Adef%20findPositionOfElement%28list,%20element_to_find_position%29%3A%0A%20%20%20%20if%20not%20isEmptyList%28list%29%20%20and%20isAvailable%28list,%20element_to_find_position%29%3A%0A%20%20%20%20%20%20%20if%20isSingleElementList%28list%29%3A%0A%20%20%20%20%20%20%20%20%20%20return%200%0A%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20position%20%3D%200%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20element%20in%20list%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20element%20%3D%3D%20element_to_find_position%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20position%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%20%2B%3D%201%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20%22Can't%20Find%20an%20Element%20in%20List%22%0A%0Adef%20isSortedList%28list%29%3A%0A%20%20%20%20if%20not%20isEmptyList%28list%29%20and%20isMonoTypeList%28list%29%3A%0A%20%20%20%20%20%20%20if%20isSingleElementList%28list%29%3A%0A%20%20%20%20%20%20%20%20%20%20return%20True%0A%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20first_element%20%3D%20findFirstElement%28list%29%0A%20%20%20%20%20%20%20%20%20%20%20%20last_element%20%3D%20findLastElement%28list%29%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20first_element%20%3C%20last_element%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20for%20element%20in%20list%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20element%20%3C%20first_element%20or%20element%20%3E%20last_element%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20False%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20True%0A%20%20%20%20%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20first_element%20%3E%20last_element%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20for%20element%20in%20list%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20element%20%3E%20first_element%20or%20element%20%3C%20last_element%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20False%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20True%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20%22Invalid%20List%22%0A%0Adef%20findTheElementInPosition%28list,%20position_of_element%29%3A%0A%20%20%20%20if%20%28not%20isEmptyList%28list%29%29%3A%0A%20%20%20%20%20%20%20if%20%28%28sizeOfList%28list%29-1%29%20%3E%3D%20position_of_element%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20return%20list%5Bposition_of_element%5D%0A%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20return%20%22Position%20is%20OutBound%22%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20%22Invalid%20List%22&cumulative=false&heapPrimitives=false&mode=edit&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&testCasesJSON=%5B%22def%20test_list_element_is_available%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''find%20the%20element%205%20in%20list'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B3,%201,%205,%202,%204%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20True%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isAvailable%28list,%205%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%20%20%20%20%22,%22def%20test_list_element_is_not_available%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''find%20the%20element%205%20in%20list'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B3,%201,%205,%202,%204%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20False%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isAvailable%28list,%206%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_list_is_mono_type_true%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Expected%20list%20is%20mono%20type'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B3,%201,%205,%202,%204%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20True%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isMonoTypeList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_list_is_mono_type_false%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Expected%20list%20is%20non%20mono%20type'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B3,%201,%205,%202,%204,%20%5C%22Six%5C%22%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20False%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isMonoTypeList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_list_is_empty%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Expected%20list%20is%20Empty'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20True%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isEmptyList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_list_is_non_empty%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Expected%20list%20is%20Non_Empty'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20False%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isEmptyList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_find_size_of_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Expected%20Size%20is%205'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B3,%201,%205,%202,%204%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%205%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.sizeOfList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_for_single_element%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Expected%20isSilgleElementList%20is%20True'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B3%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20True%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isSingleElementList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_search_for_element_in_empty_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Searching%20for%20element%203%20in%20empty%20list'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Empty%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.searcher%28list,3%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_max_element_in_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20max%20element%20is%2010'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%202,%203,%2010,%204,%207,%205,%209,%200%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%2010%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findMaxElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_max_element_in_list_empty_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Empty%20list%20but%20we%20trying%20to%20find%20element%2010'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Invalid%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findMaxElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_min_element_in_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20max%20element%20is%2010'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%202,%203,%2010,%204,%207,%205,%209,%200%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%200%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findMinElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_min_element_in_list_empty_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Empty%20list%20but%20we%20trying%20to%20find%20element%2010'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Invalid%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findMinElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_first_element_in_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20first%20element%20is%201'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%202,%203,%2010,%204,%207,%205,%209,%200%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%201%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findFirstElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_first_element_in_list_empty_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Empty%20list%20but%20we%20trying%20to%20find%20first%20element'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Invalid%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findFirstElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_last_element_in_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20last%20element%20is%201'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%202,%203,%2010,%204,%207,%205,%209,%2020%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%2020%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findLastElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_last_element_in_list_empty_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Empty%20list%20but%20we%20trying%20to%20find%20last%20element'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Invalid%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findLastElement%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_position_of_element_in_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20last%20element%20is%201'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%202,%203,%2010,%204,%207,%205,%209,%2020%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%203%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findPositionOfElement%28list,10%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_position_of_element_not_available_in_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20last%20element%20is%201'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%202,%203,%2010,%204,%207,%205,%209,%2020%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Can't%20Find%20an%20Element%20in%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findPositionOfElement%28list,50%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_the_list_is_sorted_in_assending_order%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''This%20is%20Sorted%20List'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%202,%203,%204,%205,%206,%207,%208,%209%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20True%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isSortedList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_the_list_is_sorted_in_desending_order%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''This%20is%20Sorted%20List'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B9,%208,%207,%206,%205,%204,%203,%202,%201%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20True%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isSortedList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_the_list_is_not_sorted%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''This%20is%20Non%20Sorted%20List'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%207,%203,%204,%209,%206,%202,%208,%205%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20False%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isSortedList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_the_list_is_sorted_but_list_is_empty%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''This%20is%20Non%20Sorted%20List'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Invalid%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.isSortedList%28list%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_the_element_in_position_of_list%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20Element%207%20in%205th%20position'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%2010,%203,%204,%209,%207,%202,%208,%2010%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%207%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findTheElementInPosition%28list,%205%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_the_element_in_position_of_list_position_outbound%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''List%20has%20Element%207%20in%205th%20position'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B1,%2010,%203,%204,%209,%207,%202,%208,%2010%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Position%20is%20OutBound%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findTheElementInPosition%28list,%2020%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22,%22def%20test_list_finding_the_element_in_position_of_list_but_list_is_empty%28self%29%3A%5Cn%20%20%20%20%20%20%20%20'''Empty%20List%20but%20tyring%20to%20find%20element%20in%205th%20position'''%5Cn%20%20%20%20%20%20%20%20list%20%3D%20%5B%5D%5Cn%20%20%20%20%20%20%20%20expected%20%3D%20%5C%22Invalid%20List%5C%22%5Cn%20%20%20%20%20%20%20%20actual%20%3D%20LinearSearcher.findTheElementInPosition%28list,%205%29%5Cn%20%20%20%20%20%20%20%20self.assertEqual%28expected,%20actual%29%22%5D&textReferences=false


