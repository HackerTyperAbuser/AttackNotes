Danh sách quyền, trên danh sách các quyền giá trị cấu hình quyền (ví dụ Read, Create, Delete...) được gọi là **Access Control Entity** **(ACE)**. Each ACE maps back to user, group, or process (also known as security principal) and defies rights granted to that principals. In AD environment there are two types of Access Control List (ACL):
- Discretionary Access Control List (DACL): made up of ACE that allow or deny access, when someone access an object -> system check DACL -> allow or deny access. Không có DACL cho object -> full access. Có DACL nhưng không chỏ ACE tới user, group, or process -> không có quyền cho tất cả. 
![[Pasted image 20261103143748.png]]
- System Access Control List (SACL): cho phép adminsitrators log lượt truy cập tới các object. Xem ở tab "Auditing"
![[Pasted image 20261103143855.png]]
# Enumerate ACL
PowerView
```powershell
Find-InterestingDomainAcl
```