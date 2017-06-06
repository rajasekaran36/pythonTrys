#Linear Searcher
''' python
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
            
...
