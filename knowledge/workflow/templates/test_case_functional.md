# Functional Test Case: {Feature Name}

**This file is a persistent test design document managed in Git.**

## Overview

Detailed test case definition for {Feature Name}.
Create to exhaustively cover Acceptance Criteria.

## Test Matrix

| Case ID          | Case Name                | Pre-condition | Procedure                                                             | Expected Result                                   | Aspect     |
| :--------------- | :----------------------- | :------------ | :-------------------------------------------------------------------- | :------------------------------------------------ | :--------- |
| FT-{Feature}-001 | Normal: Basic Flow       | Logged in     | 1. Access Screen X<br>2. Enter "Value" in Input A<br>3. Click Save    | Save complete message appears, data is registered | Function   |
| FT-{Feature}-002 | Abnormal: Required Check | Logged in     | 1. Access Screen X<br>2. Leave Input A empty<br>3. Click Save         | "Required" error appears                          | Validation |
| FT-{Feature}-003 | Boundary: Max Length     | Logged in     | 1. Access Screen X<br>2. Enter max length in Input A<br>3. Click Save | Save complete message appears                     | Boundary   |
