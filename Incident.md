classDiagram
direction BT
class Incident {
    guid
    orgId
    referId
    status
    priority
    occured
    created
    updated
    submited
    biReported
    requested
    reportBy
    createdBy
    updatedBy
    submitedBy
    requestedBy
    issueTypeCategory
    unfounded
    boardIncident
    needApproval
    siteId
    facilityId
    locationType
    longitude
    latitude
    notiType
    contactName
    contactPhone
    contactFax
    otherLocation
    exactLocation
    description
    confidentialComment
    boardComment
    joinInfo
    statusChangeReason
    issueType
    attachmentCount
    eventMetadata
    id
}
class Organization {
    name
    logo
    title
    subTitle
    timezone
    authType
    randomPassword
    provider
    feature
    configuration
    notiType
    smsProvider
    sFtpInviteEmail
    supportEmail
    languages
    created
    updated
    client_id_adp
    client_secret_adp
    subscriberOrganizationOID_adp
    client_id_adp_kokomo
    client_secret_adp_kokomo
    notificationEnabled
    bulkSenderEmail
    workflowOrganizationId
    workflowAccessCode
    id
}
class Role {
    guid
    orgId
    name
    authority
    isSystemRole
    code
    id
}
class SelfReport {
    orgId
    name
    active
    required
    dayOfWeek
    dayOfWeekReminder
    repeatType
    reminderTime
    notiType
    updateDuration
    siteId
    timezone
    allowUpdate
    confidential
    startDate
    endDate
    created
    updated
    createdBy
    updatedBy
    exemptVaccineTypeId
    id
}
class Site {
    guid
    orgId
    name
    siteTypeId
    status
    parentId
    costCenter
    parentCostCenter
    charterType
    contact
    fax
    address
    longitude
    latitude
    created
    updated
    createdBy
    updatedBy
    boardDistrict
    localDistrict
    siteTypeCode
    preferredCode
    locationCode
    locationName
    rtsData
    statecode
    typeOfVisitor
    reasonforVisit
    imageOverlayData
    srId
    preRegistrationStartDate
    preRegistrationEndDate
    walkInType
    isVisionFair
    isCS
    isBSAP
    isPS
    workflowMetadata
    id
}
class SiteType {
    code
    name
    id
}
class User {
    guid
    orgId
    siteId
    firstName
    middleName
    lastName
    email
    personalEmail
    phone
    status
    userTypeId
    roleId
    ssoEmployeeId
    title
    authType
    notiOpt
    bypass
    testUser
    created
    updated
    synced
    addressUpdated
    createdBy
    updatedBy
    integratedId
    suspendReason
    text1
    text2
    text3
    text4
    text5
    systemLogin
    disableLogin
    address
    contact
    dob
    consentLink
    grade
    adpAoid
    keywordSearch
    preferredFirstName
    preferredMiddleName
    preferredLastName
    workflowAccessCode
    id
}
class UserType {
    name
    incidentLevel
    id
}

Incident  -->  Organization : orgId:id
Incident  -->  Site : siteId:id
Incident  -->  User : createdBy:id
Incident  -->  User : reportBy:id
Incident  -->  User : requestedBy:id
Incident  -->  User : updatedBy:id
Incident  -->  User : submitedBy:id
Role  -->  Organization : orgId:id
SelfReport  -->  Organization : orgId:id
SelfReport  -->  Site : siteId:id
SelfReport  -->  User : createdBy:id
SelfReport  -->  User : updatedBy:id
Site  -->  Organization : orgId:id
Site  -->  SelfReport : srId:id
Site  -->  SiteType : siteTypeId:id
Site  -->  User : updatedBy:id
Site  -->  User : createdBy:id
User  -->  Organization : orgId:id
User  -->  Role : roleId:id
User  -->  User : updatedBy:id
User  -->  User : createdBy:id
User  -->  UserType : userTypeId:id
