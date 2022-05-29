# [TinyXML2]

                                                
      < [index.md]

## WRITE INTO DOCUMENT 
    1. Create XML doc                    `tinyxml2::XMLDocument xmlDoc;`
    2. Create root node                  `tinyxml2::XMLNode* pRoot = wmlDoc.NewElement(Root);`
    3. Attach it to Xmldocument          `xmlDoc.InsertFirstChild(pRoot);`
    4. Putting data in new XMLDocument
         1. Create XMLElement                        `XMLElement* pElement = xmlDoc.NewElement("IntValue");`
         2. Set Text for Element                     `pElement->SetText(10);`
         3. Add a new element as a child of          `pRoot->InsertEndChild(pElement);`
            document's root node

    * Store a float is identical to store an int.The other 
      accepted type are unsigned `int, double,bool,const char*`.

    5. Show element value                           `std::cout << pElement->GetText() << std::endl;`

## SET ATTRIBUT 
```cpp 
    pElement = xmlDoc.NewElement("Date")
    pElement->SetAttribute("day", 26);
    pElement->SetAttribute("month", "April");
    pElement->SetAttribute("year", 2014);
    pElement->SetAttribute("dateFormat", "26/04/2014");
    pRoot->InsertEndChild(pElement);
```

## ITERATE THOUGHT STD::VECTOR TO STORE INFORMATIONS
```cpp
    pElement = doc.NewElement("List");
    std::vector<int> vecList;

    for (int i=0; i <= 10; i++) {vecList.push_back(i); }

    for(const auto& item : vecList)  {
    tinyxml2::XMLElement* pListElement = doc.NewElement("Item");
    pListElement->SetText(item);
    pElement->InsertEndChild(pListElement);
    }

    pRoot->InsertEndChild(pElement); 
```

## SAVE TO XML DOCUMENT
                XMLError eResult = xmlDoc.SaveFile("saveData.xml");

## LOAD XML FILE INTO A NEW DOCUMENT
```cpp
    tinyxml2::XMLDoc doc;
    tinyxml2::XMLError eResult = xmlDoc.LoadFile("data.xml");
    tinyxml2::XMLNode* pRoot = xmlDoc.FirstChild();

    if(pRoot == nullptr) return tinyxml2::XML_ERROR_FILE_READ_ERROR;

    tinyxml2::XMLElement* pElement = pRoot->FirstChildElement("Elem1");
    if (pElement == nullptr) return tinyxml2::XML_ERROR_PASSING_ELEMENT; 
    
    int iOutInt;
    eResult = pElement->QueryIntText(&iOutInt);
    std::cout << iOutInt << std::endl;
```
## EXTRACT DATA WRITTEN WITH SET ATTRIBUTE BELOW
```cpp
    pElement = pRoot->FirstChildElement("Date");
    if(pElement == nullptr) return tinyxml2::XML_ERROR_PARSING_ELEMENT;

    int iOutDay,iOutYear;
    eResult = pElement->QueryIntAttribute("day",&iOutDay);
    eResult = pElement->QueryIntAttribute("year",&iOutYear);
    const char* attrText = nullptr;
    attrText = pElement->Attribute("month");
    std::string monthStr = attrText;
    std::cout << "Day:: " << iOutDay <<"\tMonth:" << monthStr <<  "\tYear:: " << iOutYear << std::endl;
```
 ## EXTRACT MULTI ELEMENTS WRITTEN BELOW WITH OUR VECTOR 
```cpp                             
    tinyxml2::XMLElement* pElement = pRoot->FirstChildElement("List");
    tinyxml2::XMLElement* pListElement = pElement->FirstChildElement("Item");
    std::vector<int> myList;

    for( ;pListElement != nullptr; )
    {
    int iOutListValue;
    eResult = pListElement->QueryIntText(&iOutListValue);

    myList.push_back(iOutListValue);
    pListElement = pListElement->NextSiblingElement("Item");
    }

    for(auto& elem : myList) std::cout <<elem << std::endl; 
```
