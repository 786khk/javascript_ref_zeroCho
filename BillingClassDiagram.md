```plantuml
@startuml

!define lombok_getter     class_method{+ get*()}
!define lombok_setter     class_method{+ set*(*)}
!define lombok_tostring   class_method{+ toString(): String}
!define lombok_equals     class_method{+ equals(*): boolean}
!define lombok_hashcode   class_method{+ hashCode(): int}
!define lombok_constructor class_method{+ <init>(...)}
!define lombok_allArgsConstructor class_method{+ <init>(...)}
!define lombok_noArgsConstructor class_method{+ <init>(...)}
!define lombok_jsonInclude_nonEmpty class_method{+ Include.NON_EMPTY}
!define lombok_builder class_method{+ <init>(...) }
class NhnCloudField{
    - enum NhnCloudFieldEnum
    + List<ProviderFieldListDto> getProviderFieldList()
    + List<?> getAccountTypeList()
    {static} + Partner_NecessaryInfra extends AccountArgumentDto
    {static} + OpenApi_ObjectStorage extends AccountArgumentDto
    {static} + OpenApi_ObjectStorage extends AccountArgumentDto
    {static} + OpenApi_ResourceWatcher extends AccountArgumentDto
    {static} + OpenApi_SystemMonitoring extends AccountArgumentDto
    {static} + OpenApi_CloudMonitoring extends AccountArgumentDto
    {static} + OpenApi_KeyManager extends AccountArgumentDto
    {static} + OpenApi_Volume extends AccountArgumentDto
    {static} + OpenApi_Network extends AccountArgumentDto
    {static} + OpenApi_RDS extends AccountArgumentDto
}

NhnCloudField ..|> ICloudAccount

NhnCloudField o-- NhnCloudFieldEnum
NhnCloudField o-- Partner_NecessaryInfra
NhnCloudField o-- OpenApi_ObjectStorage
Partner_NecessaryInfra --|> AccountArgumentDto
OpenApi_ObjectStorage --|> AccountArgumentDto
c --|> AccountArgumentDto
OpenApi_SystemMonitoring --|> AccountArgumentDto
OpenApi_CloudMonitoring --|> AccountArgumentDto
OpenApi_KeyManager --|> AccountArgumentDto
OpenApi_Volume --|> AccountArgumentDto
OpenApi_Network --|> AccountArgumentDto
OpenApi_RDS --|> AccountArgumentDto

enum NhnCloudFieldEnum {
OPENAPI
PARTNER
}

class Partner_NecessaryInfra {
    + Partner_NecessaryInfra()
}

class OpenApi_NecessaryInfra{

}
class OpenApi_ObjectStorage{
    +OpenApi_ObjectStorage()
}
class OpenApi_ResourceWatcher{
    +OpenApi_ResourceWatcher()
}
class OpenApi_SystemMonitoring{
    +OpenApi_SystemMonitoring()
}
class OpenApi_CloudMonitoring{
    +OpenApi_CloudMonitoring()
}
class OpenApi_KeyManager{
    +OpenApi_KeyManager()
}
class OpenApi_Volume{
    +OpenApi_Volume()
}
class OpenApi_RDS{
    +OpenApi_RDS()
}
class OpenApi_Network{
    +OpenApi_Network()
}

class OPENAPI implements ICloudAccountField{
     +List<AccountArgumentDto> getFieldList()
}
class PARTNER implements ICloudAccountField{
     +List<AccountArgumentDto> getFieldList()
}

NhnCloudFieldEnum -[hidden]-> OPENAPI
NhnCloudFieldEnum -[hidden]-> PARTNER
ICloudAccountField <|.. OPENAPI
ICloudAccountField <|.. PARTNER



interface ICloudAccountField {
    + abstract List<AccountArgumentDto> getFieldList()
}

interface ICloudAccount{
    +abstract List<ProviderFieldListDto> getProviderFieldList()
    +abstract List<?> getAccountTypeList();
}
class CredentialDto{
    {static} +  class AccountArgumentDto
    + 
}

class AccountArgumentDto {
    - String resourceTypeName
    - String resourceTypeCode
    - Integer orderNo
    - List<ArgumentStoreDto> resourceFieldList
    {static} +  AccountArgumentDto(resourceTypeName,resourceTypeCode, orderNo,resourceFieldList)
    + AccountArgumentDto setOrderNo(Integer orderNo)
    + AccountArgumentDto setResourceFieldList(List<ArgumentStoreDto> resourceFieldList)
    + AccountArgumentDto setResourceTypeName(String resourceTypeName)
    + AccountArgumentDto setResourceTypeCode(String resourceTypeCode)
    

    @NoArgsConstructor
    @AllArgsConstructor
    
}
AccountArgumentDto : +AccountArgumentDto()
AccountArgumentDto : +AccountArgumentDto(String resourceTypeName,String resourceTypeCode,Integer orderNo)

' class AccountArgumentDtoBuilder {
'     + String resourceTypeName
'     + String resourceTypeCode
'     + Integer orderNo
'     + List<ArgumentStoreDto> resourceFieldList
' }

' AccountArgumentDto "1" <-- "1" AccountArgumentDto : AccountArgumentDto

note right of AccountArgumentDto
    Lombok @Builder applied to constructor
    Lombok @@JsonInclude applied to resourceFieldList
end note

AccountArgumentDto "1" *-- "many" ArgumentStoreDto : resourceFieldList

class ArgumentStoreDto {
    @NoArgsConstructor
    @AllArgsConstructor
    lombok_setter
    - String field
    - Boolean isHeader
    - Boolean isUnique
    - String description
    -List<ArgumentFieldDto> memberList
   
    + ArgumentStoreDto(String field,Boolean isHeader,Boolean isUnique,String description, List<ArgumentFieldDto> memberList)
}

    
class ArgumentFieldDto {
    - String name
    - String value

    + lombok_getter
    + lombok_setter
}

note right of ArgumentFieldDto
    Lombok @Builder applied to constructor
end note
ArgumentStoreDto "1" *-- "many" ArgumentFieldDto : memberList

class CloudAccountDto {
    +static class ProviderFieldListDto
}

class ProviderFieldListDto {
    + lombok_getter
    + lombok_setter
    + lombok_tostring
    + lombok_equals
    + lombok_hashcode
    + lombok_constructor
    - String accountType
    - List<AccountArgumentDto> accountFieldList
    + ProviderFieldListDto( accountType,  accountFieldList)
}
RequestFieldDto "1" *-- "many" AccountArgumentDto : resourceFieldList
note right of ProviderFieldListDto
    Lombok @Builder applied to constructor
end note


class ResourceFieldDto {
    ' Lombok annotations
    ' @Getter @Setter
    + lombok_getter
    + lombok_setter
    - String field
    -@JsonProperty("isHeader") boolean isHeader
    - String value
}

class RequestFieldDto{
    + lombok_getter
    + lombok_setter
    - String resourceTypeName
    - List<ResourceFieldDto> resourceFieldList
    - String resourceTypeCode
}
RequestFieldDto "1" *-- "many" ResourceFieldDto : resourceFieldList

class CredentialResponseResultDto{
    lombok_getter
    lombok_setter
    - ResponseMetadataDto metadata
    - ResponseDataDto data
}
CredentialResponseResultDto "1" *-- "1" ResponseDataDto:data
CredentialResponseResultDto "1" *-- "1" ResponseMetadataDto:metadata

class ResponseDataDto{
    lombok_getter
    lombok_setter
    lombok_jsonInclude_nonEmpty
    - List<RequestFieldDto> credential
}
ResponseDataDto "1" *-- "many" RequestFieldDto : credential

class ResponseMetadataDto{
    lombok_getter
    lombok_setter
    - String createdTime
    - String deletionTime
    - boolean destroyed
    - Object customMetadata
    - int version
}
class CloudAccountUtils {
    final - ApplicationContext context
    + List<ProviderFieldListDto> getLoginFieldList(String providerName) throws IllegalAccessException, IllegalArgumentException, InvocationTargetException, NoSuchMethodException, SecurityException

    + List<?> getLoginFieldList(String providerName) throws NoSuchMethodException, SecurityException, IllegalAccessException, IllegalArgumentException, InvocationTargetException
}
NhnCloudFieldEnum ..|> ICloudAccountField

@enduml
