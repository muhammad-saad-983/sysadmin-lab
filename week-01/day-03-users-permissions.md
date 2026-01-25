# Day 03: Users, Groups & Permissions

## 🎯 Task
Simulate a team environment where files created by any user in a shared folder are automatically owned by the group.

## 🛠️ Implementation
1. **User Setup:**
   - Created user `intern` (`adduser`).
   - Created group `ops` (`groupadd`).
   - Added intern to ops (`usermod -aG ops intern`).

2. **Directory Setup:**
   - Location: `/srv/shared`
   - Ownership: `root:ops`
   - Permissions: `2775` (SetGID + RWX for Group).

## 🧠 Concept: SetGID (The '2' in 2775)
Normally, new files take the user's primary group (`intern:intern`).
By setting the **SetGID bit** on the parent directory, new files inherit the directory's group (`intern:ops`). This ensures all team members can edit collaborative files.

## ✅ Verification
- Logged in as `intern`.
- Created file `/srv/shared/test.txt`.
- `ls -l` confirmed group owner is `ops`.
