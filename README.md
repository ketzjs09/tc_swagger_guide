**swagger:** Should be set to the swagger version in use. Value should be left as is unless the swagger version is updated.
*Example*
  >"'swagger: 2.0'"

**info:**
  * **version:** This should contain the proper version of the swagger file with exactly reflects its current iteration. For every update, the version should be updated using the basic rule of - 
  x - major release
  y - minor release
  z - build number, where the version is x.y.z 

    *Example*
      >"version: 1.2.9"


  - **title:** This should contain the title of the API. For new APIs and in APIs where change in the title can be considered, the title should be assigned after proper consideration. It should clearly reflect the core use-case of the API. Practically, for most existing APIs, the title Value should be left as is, i.e identical to the legacy title to avoid any confusion for developers acquainted with previous versions. 

    *Example*
      >"title: Challenge API V5"

  - **description:**
    This should provide a clear and concise description of the API and a high level overview of the concept and model encapsulated by the API. Additional overaching information such as pagination and access controls etc should be shared if available.

    *Example*
      >"description: A challenge is a contest hosted in the Topcoder platforms which is usually open to the public for participation. There are several kinds of challenges at Topcoder and they are mostly related to tech and design, and are comprised of several stages such as registration, submission review etc. <br/>
      Challenges are usually a part of a real world project for a Topcoder client. Typical projects revolve around building applications, websites, UI/UX and data science solutions for clients who're looking to leverage the capabilities of the crowd and participate in the passion economy."


**tags:** Value should be left empty. Paths can be grouped into groups and each group can have a corresponding tag. These tags can be defined in the root level as follows. In general, groups and hence tags should reflect some kind of actual grouping of the concepts/paths being defined. Grouping shouldn't be arbritrary or contrived.

For more information, please refer to https://swagger.io/docs/specification/grouping-operations-with-tags/ 

Important - The groups will be rendered in any swagger viewer in the order in which it is defined here under the 'tags' section. So proper consideration should be given to desired order of the groupings, and they should be listed below in that order.


  * **- name:** Should contain the name of the group tag. This tag should be in use by at least one path in the current swagger file. If any tag is not required anymore after an update to the API/swagger file, that tag should be removed.
  **description:** Should contain a concise description of tag. This information will be displayed at the top of the group. 
  **externalDocs:**
    - **url:** Should contain a link to any external resource if available. This should be populated by the relevant links that contain further information about this group

  * **- name:** Should contain the name of the another group
    **description:** Should contain the description of the group
    **externalDocs:**
      - **url:** Should contain the link of the group

  *Example*
  > **- name:** ChallengeTypes
    **description:** Paths concerning the different types of challenges at Topcoder.  
    **externalDocs:**
      - **url:** https://help.topcoder.com/hc/en-us/articles/217481558-Development-Challenge-Types"
  

**host:**  Should be set to the host address.
*Example*
  >host: api.topcoder.com
  
**basePath:** Should be set to the base path under the host address. Most probably will continue to reflect the current version of the API
*Example*
  >basePath: /v5

**schemes:** The value should be left empty. This should contain the transfer protocols used by the API. http, https, and WebSocket schemes ws and wss are supported by swagger. 
*Example*
 > schemes:
  -http
 -https"

**securityDefinitions:** The value should be left empty.  This should encapsulate all security schemes (authentication types) supported by the API.
  * **bearer:** This value should be left empty. This should encapsulate properties related to bearer security schemes. For more information about authentication, refer to: https://swagger.io/docs/specification/2-0/authentication/
    * **type:** This should contain the type of authentication to be used.
    *Example*
      >type: apiKey ()

    * **name:** This should contain a descriptive name of the  authentication.  
    *Example*
      >name: API Key Authorization

    * **in:** This should contain the location where the API key should be looked for. 
    *Example*
      >in: header

**paths:** Value should be left empty. This encapsulates the paths in the API
  * **/<path_name>:** Value should be left empty. The name of this property should reflect the actual name of the path of the API
  *Example*
    > /challenge-types:
    * **<request_type>:** Value should be left empty. The name of this property should indicate the type of request - i.e. get/post/put/delete
    *Example*
      > get:
      * **tags:** Value should be left empty. This encapsulted the tag under which this path should be encapsulated when rendering by a viewer.

        - <tag_name> Only property name should be set.Value should be empty.
          *Example*
          >ChallengeTypes

      * **description:** Should contain a concise description of the API path.
        *Example*
          > description: Returns a list of all challenge types hosted at Topcoder
      * **produces:**
          - Should contain the format of response to be expected from the path.
          *Example*
            > produces : application/json
      * **parameters:** Value should be left empty. This should encapsulate the different parameters inside the path /<path_name>. For further reference: https://swagger.io/docs/specification/2-0/describing-parameters/
        * **\$ref:** One or more of these $ref references can be used to refer to existing parameters that need to be defined at the root level parameter. Parameters have been described later.
        *Example*
          > '$ref: #/parameters/perPage'
        * **name:** Should contain the name of the parameter. Names should be chosen to be concise and precisely indicating the intended parameter.
                *Example*
          > name: description
        * **in:** Should contain the the location where the parameter should be found. That is, whether the parameter should be looked for in the query section or the path. Possible values can be query/path/header/cookie. For further reference: https://swagger.io/docs/specification/2-0/describing-parameters/
        *Example*
          > in: query

        * **description:** Should contain detailed enough information about the intended use of the parameter, in addition other details such case-sensitivity, whether partial matches are allowed, etc.
        *Example*
          > description: Name of the specific challenge type that's required. Can case-sensitive and partial matches are allowed.

        * **required:** Should contain the boolean value indicating whether the parameter is required or not.
        *Example*
          > required: false
        
        * **type:** Should contain the datatype of the value to be entered for this parameter.
        *Example*
          > type: string
      * **responses:** Value should be left empty. This should encapsulate the attributes related to the responses. For further reference, please refer to: https://swagger.io/docs/specification/2-0/describing-responses/
        * **<response_code>**: Value should be left empty. The name of this property should indicate the potential response code that has been implemented by the API. All response codes that are implemented should be listed using similar structures described below. List of response codes can be found here: https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html
          *Example*
          > '200':

            **description:** Description/interpretation of the response code mentioned above. The definitions can be found here: https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html
            **schema:** The value should be empty. This will encapsulate the information about the schema of the response.
            *  **type:** Should contain the datatype of the schema. For the complete list of types, refer to the link shared above.
            * **items:** Should contain the schema that describes the type and format of array items.
            * **\$ref:** Should contain the the internal link to the definition that should be referenced. When a definition is reference, the schema defined in it is adopted by the intended schema of this response.
              *Example*
              > $ref: #/definitions/ChallengeType

            **headers:** The value should be empty. This should encapsulate any custom headers to provide additional information in addition to the response body. For example, a rate-limited API may provide the rate limit status via response headers as follows:
            - **<header_name>** The value should be empty. This should encapsulate the name of the header, which in should be a hypher separate phrase or a word, generally starting with an 'X-'.
                *Example*
              > **X-Page:**
              or 
              **X-RateLimit-Limit:**

            - **type:** This should describe the datatype of the response header. 
            *Example*
              > type: integer

            - **description:** This should contain a clear and if required elaborate description of the response header, considering that the response header along with the response body might be one of the most read parts of the API reference.
  
**parameters:**
* **<parameter_name>**Value should be left empty. This should encapsulate the different parameters inside the path /<path_name>. These parameters can be referenced using \$ref by the parameter definitions under the 'parameter' property of path definitions.  For further reference: https://swagger.io/docs/specification/2-0/describing-parameters/.
    *Example*
    > perPage:

    * **name:** Should contain the name of the parameter. Names should be chosen to be concise and precisely indicating the intended parameter.
    *Example*
        > name: perPage
    * **in:** Should contain the the location where the parameter should be found. That is, whether the parameter should be looked for in the query section or the path. Possible values can be query/path/header/cookie. For further reference: https://swagger.io/docs/specification/2-0/describing-parameters/
    *Example*
        > in: query
    * **description:** Should contain detailed enough information about the intended use of the parameter, in addition other details such case-sensitivity, whether partial matches are allowed, etc.
    *Example*
        > description: Name of the specific challenge type that's required. Can case-sensitive and partial matches are allowed.
    * **required:** Should contain the boolean value indicating whether the parameter is required or not.
    *Example*
        > required: false
    * **type:** Should contain the datatype of the value to be entered for this parameter.
        > type: integer
    * **default:** Should contain the default value of the parameter in consideration.
    *Example*
        > default: 20
    * **maximum:** Should contain the maximum permissible value of the parameter in consideration.
    *Example*
        > maximum: 100
    
**definitions:** The value should be empty. This should encapsulate the data model definitions. These data models can be leveraged by the other parts of the swagger definitions above. 
*  **<model_name>** The value should be empty. This should contain the name of the model. The name should generally be written with camel-casing and the name should be descriptive and yet not too long. Multiple models/schema can be listed.
*Example*
    > ChallengeType:

    * **type:** This should contain the type of the model schema being defined. For additional reference of datatypes, refer: https://swagger.io/docs/specification/data-models/data-types/
    *Example*
        > type: object
    * **<schema_selector_keyword>:** This should be one of the following - 
    oneOf – validates the value against exactly one of the subschemas
allOf – validates the value against all the subschemas
anyOf – validates the value against any (one or more) of the subschemas
    *Example*
        > allOf:
      * **\- type:**  This should contain the type of the sub-schema being defined. Similar to the type property described above.
      *Example*
        > type: object
       *  **properties:**
            > properties: The value should be empty. This should encapsulate the list of properties of the object built using the current schema.
          * **<property_name>** The value should be empty. The property should be named based on the internal implementation of the API.
          *Example*
            > id:
            * **type:** This should contain the type of the property. The list of types is identical to the other types mentioned above.
            *Example*
                > type: string
            * **description:** This should contain an informative yet concise description of the property name. 
            *Example*
                > description: The challenge type ID. 
                Note - This kind of terse descriptions should be used only if the term (challenge type ID in this case) has already been discussed in the document. Otherwise, use a more detailed description.
            * **format:** This should contain the string format of the property. For further details, refer to the String Formats section here: https://swagger.io/docs/specification/data-models/data-types/
            *Example*
                > format: UUID


        * **- $ref:** This should contain references to other definitions of models. Though care should be taken that complex cyclical references are not created. For more information on \$ref, including additional syntax details, refer to the documentation here: https://swagger.io/docs/specification/using-ref/ (Note - The documentation is listed under Swagger version 3.0, but are largely applicable to version 2.0)
      *Example*
             > \- $ref: '#/definitions/ChallengeTypeData'

        * **required:** The value should be left empty. This should encapsulate the list of properties are essential for the model. 
      **- <required_property_name>** - This should contain the name of the essential property. Multiple essential properties can be listed in order under the the 'required' property.
      *Example*
            > \- id
        

