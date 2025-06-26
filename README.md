# Prevent User Deletion If Assigned To An Incident

## 📋 Project Overview

This ServiceNow guided project implements a safeguard mechanism to prevent the deletion of users who are actively assigned to incidents in an IT Service Management environment.

## 🎯 Problem Statement

In an IT Service Management environment, users are frequently assigned to incidents for issue resolution and tracking. However, the current system lacks a validation mechanism to prevent the deletion of a user who is still actively assigned to incidents. This can lead to:

- Broken data references
- Loss of accountability  
- Disruption in workflow continuity

**Solution**: Implement a safeguard that prevents such deletions unless all assigned incidents are closed or reassigned.

## 🚀 Project Workflow

The project follows these key phases:

### Phase 1: User Creation
- **Step 1**: Create Test Users
- Set up test user accounts for validation scenarios

### Phase 2: Incident Assignment  
- **Step 2**: Assign Incident To User
- **Step 3**: Assign Incidents
- Create incidents and assign them to test users

### Phase 3: Business Rule Implementation
- **Step 4**: Business Rule Creation
- **Step 5**: Create Business Rule
- Implement the core validation logic

### Phase 4: Testing & Validation
- **Step 6**: Test Deletion
- **Step 7**: Attempt To Delete Assigned User
- **Step 8**: Test With Unassigned User  
- **Step 9**: Attempt To Delete Unused User
- **Step 10**: Conclusion

## 🛠️ Implementation Steps

### Prerequisites
- ServiceNow instance access
- Admin or developer role permissions
- Basic understanding of ServiceNow Business Rules

### Step-by-Step Implementation

#### 1. User Creation Phase
```
Navigate to: User Administration > Users
Create test users for validation scenarios
```

#### 2. Incident Assignment Phase
```
Navigate to: Incident > Create New
Assign incidents to the created test users
Document incident numbers for testing
```

#### 3. Business Rule Creation
```
Navigate to: System Definition > Business Rules
Create new Business Rule with:
- Table: User [sys_user]
- When: Before Delete
- Condition: Check for active incident assignments
- Script: Validation logic to prevent deletion
```

#### 4. Testing Phase
```
Test Scenario 1: Attempt to delete user with active incidents
Expected Result: Deletion prevented with error message

Test Scenario 2: Attempt to delete user without active incidents  
Expected Result: Deletion allowed
```

## 📝 Business Rule Logic

The business rule should implement the following logic:

1. **Trigger**: Before user deletion
2. **Validation**: Check if user has active incident assignments
3. **Action**: 
   - If active incidents exist → Prevent deletion + Show error message
   - If no active incidents → Allow deletion

## 🧪 Testing Scenarios

### Scenario 1: User with Active Incidents
- **Action**: Attempt to delete user assigned to open incidents
- **Expected**: Deletion blocked with informative error message

### Scenario 2: User without Active Incidents  
- **Action**: Attempt to delete user with no incident assignments
- **Expected**: Deletion proceeds successfully

### Scenario 3: User with Closed Incidents Only
- **Action**: Attempt to delete user with only resolved/closed incidents
- **Expected**: Deletion allowed (closed incidents don't block deletion)

## 📊 Success Criteria

- ✅ Business rule successfully prevents deletion of users with active incidents
- ✅ Users without active incidents can be deleted normally
- ✅ Clear error messages inform administrators of the restriction
- ✅ System maintains data integrity and workflow continuity

## 🔧 Technical Considerations

### Database Impact
- Maintains referential integrity
- Prevents orphaned incident records
- Ensures audit trail completeness

### Performance
- Minimal impact on system performance
- Efficient query to check incident assignments
- Runs only during user deletion attempts

### Error Handling
- User-friendly error messages
- Proper logging for audit purposes
- Graceful handling of edge cases

## 📚 Additional Resources

- ServiceNow Business Rules Documentation
- IT Service Management Best Practices
- Data Integrity Guidelines
- User Management Policies

## 🤝 Contributing

This project is part of a ServiceNow guided learning experience. Follow the structured approach outlined in the project workspace for optimal learning outcomes.

## 📄 License

This project is created for educational purposes as part of ServiceNow University training.



