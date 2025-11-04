![GSoC @ FOSSology](/gsocHeader.png)


<h1 align="center">🌟 My GSoC 2025 Journey with FOSSology 🌟</h1>

<p align="center">
  This repository documents my entire journey as a <b>Google Summer of Code 2025</b> contributor with 
  <a href="https://www.fossology.org/" target="_blank">FOSSology</a>.  
  From proposal to contributions, weekly updates, and the final report — everything is organized here.
</p>

---

## 📌 About the Project
This year, I'm working with **FOSSology** under GSoC 2025 on **LicenseDB Platform Improvements**.  
The project focuses on enhancing LicenseDB with robust features like database migrations, rich text handling, Swagger 3.0 integration, structured logging, better search, and standardized API responses.

---

## 🛠️ Deliverables

- [x] **Database Migrations**  
  - Add support for database migrations using [golang-migrate/migrate](https://github.com/golang-migrate/migrate).
- [x] **Mail Notifications**  
  - Notify **admins**, **license creators**, and **project owners** when a license gets updated.
- [x] **Refresh Token Functionality**  
  - Implement refresh token support for secure and seamless authentication.
- [x] **New Monorepo Setup**  
  - Restructure the project into a unified **backend + frontend monorepo**.
- [x] **Minor Endpoint Improvements**
  - Add **changelogs** for user endpoints.
  - Provide **top X licenses/obligations** with similar text.
  - Improve **logging** and REST API responses.
- [x] **Test Coverage & Documentation**  
  - Improve **unit**, **functional**, and **API** test coverage.
---
### ✅ Database Migrations  
**PR:** [fossology/LicenseDB – #134](https://github.com/fossology/LicenseDb/pull/134)

#### 📍 Background  
In the context of the LicenseDB project, database migrations are essential to evolve the database schema reliably as new features get introduced. Before this work, LicenseDB lacked a standard migration system, making schema changes risky and non-versioned.

#### 🎯 Objective  
- Introduce database migration support using `golang-migrate/migrate`.
- Enable version-controlled, reversible, and safe schema upgrades.
- Ensure compatibility with existing and future database changes.

#### 🛠️ Technical Approach  
- Added a dedicated `migrations/` folder with versioned migration files (e.g., `0001_init.up.sql`, `0001_init.down.sql`).
- Integrated a migration runner to apply migrations on startup or via CLI.
- Added rollback support using `.down.sql` scripts.
- Enhanced error handling + logging for migration failures.
- Documented usage in README with guidelines for creating and running migrations.


#### 🧾 Outcome  
- Successfully integrated a robust schema migration system into LicenseDB.
- Developers can now safely introduce and track schema changes with version history.
- Reduced deployment risks and established a scalable foundation for future features.

---

### 🧪 Test Environment Setup & E2E Test Coverage

**PR:** https://github.com/fossology/LicenseDb/pull/137

**PR:** https://github.com/fossology/LicenseDb/pull/161

To ensure reliable and reproducible testing for the LicenseDB backend, I introduced a standardized test environment for both **local development** and **GitHub Actions CI**, along with end-to-end (E2E) test coverage.

---

#### ✅ Local & CI Test Environment

Previously, setting up tests required manual DB configuration, which caused inconsistent results.  
The new setup automates the entire testing workflow.

**Key Improvements:**
- Automatic creation of a **test PostgreSQL database**
- Database migrations applied before test execution
- Test data (admin, users, license creators) seeded automatically
- Automatic cleanup after tests to ensure isolation

**Run full backend test suite locally:**
```bash
go test ./...
```

This ensures developers can run tests on any machine with **one command**, without any extra setup.

### 🧪 E2E Test Coverage (~60–70%)

To validate real application behaviour rather than isolated unit scenarios, I added **end-to-end tests** covering major backend flows.

**Coverage Includes:**
- Authentication and token workflow  
- License creation, update, and retrieval  
- Migration compatibility testing  
- API behaviour with real PostgreSQL interactions  

This increased backend test coverage to **~60–70%**, providing greater stability and confidence in future development.

---
### 🔧 Minor Endpoint Improvements

As part of enhancing the API usability and maintainability, several improvements were made to user-related endpoints, logging, and data-fetching workflows.

**PR:** https://github.com/fossology/LicenseDb/pull/140

**PR:** https://github.com/fossology/LicenseDb/pull/144

---
#### 📜 Changelogs for User Endpoints

Added support for **endpoint-level changelogs**, allowing users and admins to track what changed, when, and by whom.  
This increases transparency across updates made to user profiles or roles.

**Key Benefit:** Easier auditability and traceability of user actions.


#### 🔍 Fetch Licenses & Obligations by Text

Implemented a new feature to **fetch existing licenses and obligations based on text input**.  
This allows developers and admins to quickly find similar licenses or obligations using text queries, improving the license comparison and reuse workflow.

**Use Case Examples:**
- Search for an existing license before adding a new one  
- Compare obligations with similar text  


#### 📝 Improved Logging with Zap

Replaced standard logging with **Zap Logger** for structured, performant, and context-rich logs.

**Enhancements Achieved:**
- Consistent log formatting across services  
- JSON-structured logs for better observability  
- Easier debugging and log filtering in production

**(Added Zap with the Refresh Token and Messaging System)**



