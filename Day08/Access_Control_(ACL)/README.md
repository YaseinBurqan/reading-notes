# Access Control (ACL)

# Access control lists (ACL)

    An ACL is a means of defining access rights by a given user or user group, to a specific object, such as a document. As a simple example, an ACL could be used to allow users from one department to make changes to a document, while only allowing users from other departments to read the document.

## RBAC

    Role-based access control (RBAC) is a policy-neutral access-control mechanism defined around roles and privileges. RBAC can be used to manage security in large organizations with hundreds of users and thousands of permissions. NIST study has demonstrated that RBAC addresses many needs of commercial and government organizations.

In a typical small company, management of access rights is casual at best, even "one size fits all" in some cases. If we can't get this right, our chance of having reasonably secure systems is pretty small. The solution to this problem is called role-based access control (RBAC).

With the proper implementation of RBAC, the assignment of access rights becomes systematic and repeatable. It is also much easier to audit user rights, and to correct any issues identified. RBAC arguably offers a more simplified and manageable approach, given that privileges of a user are granted with a simple effort.

## RBAC implementation

    1. Inventory your systems
    2. Analyze your workforce and create roles
    3. Assign people to roles
    4. Never make one-off changes
    5. Audit

    Identify what resources you have for which you need to control access. Analyze your workforce and create roles. Assign people their access rights and keep them as simple and stratified as possible. Many healthcare organizations use RBAC to define exactly what access to medical records each type of clinician may need. Given the large number of staff members in well stratified roles, RBAC is an efficient way to control record access. There are tools that can help with setting up RBAC.

## Role-based access control

    Role-based access control (RBAC) is a policy-neutral access-control mechanism defined around roles and privileges. RBAC can be used to manage security in large organizations with hundreds of users and thousands of permissions. NIST study has demonstrated that RBAC addresses many needs of commercial and government organizations.

## Design

    Within an organization, roles are created for various job functions. The permissions to perform certain operations are assigned to specific roles. Users acquire the permissions needed to perform system functions through their role assignments. Management of individual user rights becomes a matter of simply assigning appropriate roles to each user's account.

Three primary rules are defined for RBAC:

- Role assignment: A subject can exercise a permission only if the subject has selected or been assigned a role.

- Role authorization: A subject's active role must be authorized for the subject. With rule 1 above, this rule ensures that users can take on only roles for which they are authorized.

- Permission authorization: A subject can exercise a permission only if the permission is authorized for the subject's active role. With rules 1 and 2, this rule ensures that users can exercise only permissions for which they are authorized.

## Relation to other models

    RBAC is a flexible access control technology. Unlike context-based access control (CBAC), RBAC does not look at the message context (such as connection's source) RBAC has also been criticized for leading to role explosion in large enterprise systems because roles are inherently assigned to operations and data types.

## Comparing to ACL

    Access control lists (ACLs) are used in traditional access-control systems to affect low-level data-objects. RBACs assign permissions to operations which change the direct-relations between several entities. An operation might be to 'create a credit account' or 'populate a blood sugar test' record.

## Attribute-based access control

Attribute-based access control or ABAC is a model which evolves from RBAC to consider additional attributes in addition to roles and groups. In ABAC, it is possible to use attributes of:

    - the user e.g. citizenship, clearance,
    - the resource e.g. classification, department, owner,
    - the action, and
    - the context e.g. time, location, IP.

ABAC is policy-based in the sense that it uses policies rather than static permissions to define what is allowed or what is not allowed.

## Use and availability

Using RBAC to manage user privileges (computer permissions) within a single system or application is widely accepted as a best practice. The NIST RBAC model was adopted as a standard by INCITS as ANSI/INCITS 359-2004 and has been extended for enterprise use.
