# Sanity Checklist (Master)

**This file is a persistent checklist managed in Git.**

## Overview

A list of minimum test items to verify the health of the project.
Update this file when check items increase or decrease due to spec changes or new features.

## Test Items

| ID     | Category | Item                 | Expected Result                                          | Priority | Note |
| :----- | :------- | :------------------- | :------------------------------------------------------- | :------- | :--- |
| ST-001 | Basic    | Server Start         | Starts without error and Health Check API returns 200 OK | High     |      |
| ST-002 | Basic    | Top Page             | Top page renders correctly                               | High     |      |
| ST-003 | Auth     | Login                | Can login with correct credentials                       | High     |      |
| ST-004 | Auth     | Logout               | Redirects to login page after logout                     | High     |      |
| ST-005 | Feature  | Create {MainFeature} | {MainFeature} is created and saved to DB                 | High     |      |
