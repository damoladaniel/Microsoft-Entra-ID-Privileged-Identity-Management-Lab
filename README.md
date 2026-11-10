# Microsoft Entra ID Privileged Identity Management Lab

## Enforcing Multifactor Authentication with Privileged Identity Management & Sign-In Log Validation

### Project Summary:
This lab will demonstrate how to design , deploy and enforce Entra ID Conditional Access Policy that requires MFA. It will follow this workflow:

* Configuring a Just in time Admin access (Global Administrator) to the admin
* Create Conditional Access policy
* Safe deployment using Report Only Mode
* Live enforcement
* Real sign and testing
* Log monitoring

  ## Security Objectives

* Enforce MFA to all users
* Reduce attack surface by blocking weak authentication paths
* Secure adminisitrative actions by employing PIM
* Validate controls using identity telemetry
* Simulate SOC style identity verification
* Log collection and analysis


## Tools and Environment

- Microsoft Entra ID (P1 or P2)
- Standard User
- Break Glass admin
- MFA
- Azure Portal

## Lab Execution - Step by Step

### Step 1 - Enforce PIM to the admin account

1. Open PIM ( Microsoft Entra ID --> Privileged Identity Management --> My Roles)
2. Search Global Administrator
3. Activate Global Administrator for User "Admin Breakglass"
4. Approve MFA

   
 <img width="1605" height="375" alt="AdminBreak Glass Global Admin Role" src="https://github.com/user-attachments/assets/2e918e9b-e7df-4040-a0dc-0e4d9e53a960" />

### Step 2 - Create a Condition Access Policy

Path: Microsoft Entra ID → Protection → Conditional Access → Policies

- Click: + New policy

- Policy name:
- CondAccess01 – Require MFA for all users Users:

- Include → All users
- Exclude → Break-glass administrator
- Target resources:

- All cloud apps

<img width="1893" height="649" alt="Screenshot 2026-11-03 220939" src="https://github.com/user-attachments/assets/4ccdc22c-d12c-4a02-8c2c-10cdff0a26d7" />

- Configure Grant control to "Require multi-factor authentication"

- For multiple controls select "Require one of the selected controls"
- Deploy in "Report Only Mode
- click Create
  <br> </br>
<img width="1878" height="829" alt="Screenshot 2026-11-03 221155" src="https://github.com/user-attachments/assets/5d36a266-74ec-4e7b-9f62-493f285dcc78" />

### Step 3 - Live Sign-In Test

The purpose of the Live sign in test is to confrim that MFA is enforce during real authentication

- Open an incognito Browser window
- Go to https://portal.azure.com
- Sign in as Client User

#### What is expected:
- It should prompt for password
- Upon sign in, it should ask to change password
- It should ask to register in Authenticator (If first time user)
- It should request MA number match
- If succesful, it should log in
<br></br>

<img width="2351" height="952" alt="Screenshot 2026-11-04 144515" src="https://github.com/user-attachments/assets/9edcd8ee-1232-4284-bb17-9c57a9309058" />

<br></br>

<img width="1781" height="726" alt="Screenshot 2026-11-04 144523" src="https://github.com/user-attachments/assets/c0d19293-8762-4065-bf68-5f90124b4df9" />

<br></br>
<img width="748" height="672" alt="Screenshot 2026-11-04 144538" src="https://github.com/user-attachments/assets/c73ebb65-f0a8-4659-8a9f-b1aa9ba5c854" />


### Step 4 - Log Validation
Microsoft Entra ID → Monitoring → Sign-in logs

<img width="268" height="666" alt="image" src="https://github.com/user-attachments/assets/33e31700-2be7-4ba3-98ca-6b2086bad4b5" />

<br></br>

<img width="2519" height="856" alt="image" src="https://github.com/user-attachments/assets/9ff4adc2-5aa3-4c38-9548-8c17c936e7c7" />

<br></br>

<img width="817" height="319" alt="image" src="https://github.com/user-attachments/assets/2528b774-abdc-44fe-b3e4-88113644d499" />

## I also intentionally tried wrong password attempts
-Open new incognito/private window
-Go to: https://portal.azure.com
-Enter Felipe’s email
-Enter an incorrect password on purpose

##### Expected Behavior:

- Password rejected
- Sign-in fails


<br></br>

<img width="797" height="81" alt="Screenshot 2026-11-04 155310" src="https://github.com/user-attachments/assets/b5e4d7c1-9499-4062-a304-2e0055abb5fe" />

<br></br>

### Security Outcomes
- MFA was successfully enforeced and Tested
- Conditional Access verified
- Privileged Identity Management protects admin access
- Authentication flow validated
- Audit documented via sign in logs

### Skills Demonstrated
- Microsoft Entra Conditional Access
- Privileged Identity Management (PIM)
- MFA
- Zero Trust access control
- Audit logging
