
**PROJECT OVERVIEW:  PROPERTY MANAGEMENT SYSTEM**

*Objective*:To create a modern, interactive, and fully-featured property management web application for businesses that manage multiple properties, -floors, and units. The system will help property owners and clients manage, explore, and lease/rent properties efficiently while providing intelligent -insights and interactive tools.

----------
**Features**

##  *User Roles & Authentication with Tenant Access to Available Properties*
**Feature**: User Roles & Authentication with Tenant Access to Available Properties
**User Login**
-User does: Opens the login page and enters credentials (email/password).
-System does: Verifies credentials using JWT and identifies the user role (Admin, Manager, Tenant).
-Sytsem does: Grants access based on role.
**Role-Based Access Control**
-System does: Determines feature access for each role:
-Admin: Full access – manage properties, tenants, leases, payments, maintenance, bookings.
**Manager/Staff**: Limited access – handle daily operations.
**Tenant:**
-Can view their own unit details, lease info, upcoming payments, and schedule visits.
-Can also browse all other available properties with details like unit size, amenities, availability, but cannot see sensitive info like occupancy of other tenants.
**Conditional Frontend Rendering**
-System does: Shows/hides pages and buttons depending on the logged-in user’s role.
**Tenant view:**
-Full access to their own property data.
-Read-only access to other available properties, with interactive filters and map view.
**Optional Login Convenience**
-User does: Can log in using Google/OAuth if enabled.
-System does: Authenticates via OAuth and assigns the correct role.
---

##  *Property Manager Assignment System*
**Feature**: Property Manager Assignment System

**What the System Does**
-Allows Owners to assign Managers to specific properties.
-Automatically creates a restricted Manager account.
-Ensures Managers only access the properties assigned to them.
-Allows Owners to remove or replace managers anytime.
-Keeps an activity log to track manager actions.
-How Users Interact With It
**Owner Actions**
-Owner logs into their Owner Dashboard.
-Selects a property → clicks “Manage Managers.”
-Clicks “Add Manager.”
-Enters Manager details (name, email, phone).
-Selects which property the manager will handle.
-Saves.
**System Actions**
-Creates a Manager account with role = manager.
-Links manager to that specific property only.
-Sends login details to Manager via email/SMS.
-Updates the property to show the assigned manager.
-Restricts access so Manager sees only assigned properties.
**Manager Actions**
-Manager logs into the Manager Portal.
-Sees only the properties assigned by the Owner.
**Handles**:
-Maintenance requests
-Tenant interactions
-Visit bookings
-Unit updates
-Approvals for their assigned property only
**System Updates**
-Tracks manager activity.
-Notifies Owner of important actions (e.g., maintenance completed).
-Does not allow Manager to edit properties that they do NOT manage.
**Owner Reassignment Flow**
-Owner clicks “Manage Managers” on a property.
-Clicks Remove Manager or Change Manager.
-Assigns a new manager.
**System Response**
-Previous manager loses access instantly.
-New manager gets immediate access.
-Activity logs update.

---

## *Buildings & Properties Management*

**Property Creation & Editing**
-Admin does: Opens the property management dashboard and clicks “Add Property.”
-Admin does: Fills in property details (name, address, number of floors, amenities, etc.) and uploads images/floor plans.
-System does: Saves property information in MongoDB and uploads media files to AWS S3.
-System does: Links images, documents, and floor plans to the property record.
**Property Display to Users**
-Tenant / Potential Client does: Browses the list of properties or searches using filters (location, amenities, size).
-System does: Fetches property details from the database and media from AWS S3.
-System does: Displays an interactive gallery with images, floor plans, and listed amenities.
**Floor & Unit Integration**
-System does: Shows the number of floors and available units for each property.
-User does: Clicks a floor to see available units (partial or full) with their sizes and amenities.
**Interactive Features**
-User does: Can click images, floor plans, or amenity icons for more details.
-System does: Opens modals or pages with detailed information, virtual tours, or 3D floor exploration if available.
**Security & Permissions**
-System does: Only admins can add or edit properties.
-System does: Tenants or clients can view details but cannot modify any property data.
**Outcome**:
-Admins can manage all property data efficiently with images, floor plans, and amenities.
-Tenants and clients can browse properties interactively, explore floors, and see available units clearly.


##  *Floors & Units Management*

**Floor Selection**
-User does: Selects a property to explore and chooses a specific floor (e.g., Floor 1).
-System does: Fetches all floor details from the database, including total square footage and occupancy status.
-System does: Displays available units on that floor in an interactive map or table format, highlighting which units are fully or partially available.
**Unit Selection & Allocation**
-User does: Selects one or more units they want to lease and specifies the square footage required.
-System does: Checks availability for the selected units and calculates remaining space.
-System does: Updates the unit status dynamically, showing partially occupied units and remaining space for other users.
**Multi-Floor Selection**
-User does: Can select additional floors if needed.
-System does: Displays all available units on each selected floor and updates availability in real-time.



## *Advanced Filters & Search*
**Feature**: Advanced Filters & Search

**User Sets Filters**
-User does: Opens the filter panel and selects criteria such as:
-Availability (immediate or from a specific date)
-Location (city, area, or radius from current location)
-Nearby distance from user
-Amenities (gym, cafe, parking, etc.)
-New buildings
-System does: Records the selected filter parameters.
**Filter Processing**
-System does: Queries MongoDB using the selected filter parameters to fetch matching properties.
**Display Results**
-System does: Updates the property list view and map view in real-time to show only matching properties.
-User does: Browses the filtered results and clicks on properties for more details.
**Optional Features**
-System does: Highlights new buildings or nearby amenities on the map.
-System does: Allows sorting by rent, size, or availability within filtered results.
**Outcome:**
-Users can quickly find properties matching their exact preferences.
-Enhances usability by providing dynamic filtering and map integration.
-Supports efficient property discovery for tenants and potential clients.


-------



##  *Property Comparison*
**Feature**:Property Comparison

**Selecting Properties to Compare**
-User does: Browses the property listings and selects multiple properties they want to compare.
-System does: Records the selected properties and fetches their details from MongoDB.

**Displaying Comparison**
-System does: Displays a side-by-side comparison table or card layout showing key details for each property:
-Rent amount**
-Unit/floor sizes
-Amenities (gym, cafeteria, parking, etc.)
-Floor plans or images
-Availability status
**User Interaction**
-User does: Reviews the table/cards to evaluate differences between properties.
-User does: Can click on individual properties for more detailed views or to schedule visits.
**Optional Features**
-System does: Highlights differences or best options based on user preferences.
-System does: Allows filtering or sorting within the comparison table (e.g., lowest rent, largest units, nearest location).
**Outcome**:
-Users can easily compare multiple properties in one interface.
-Helps tenants or potential clients make informed decisions quickly.
-Enhances the usability and attractiveness of the property management platform.

-------


## *Smart Availability & Partial Unit Booking*
**Feature**: Smart Availability & Partial Unit Booking 

-System loads all floors and units with real-time available sq ft.
-Calculates how much space is left for every unit.
-Prevents overbooking and updates availability instantly when someone books.
**User Flow**
-User selects a property
-System displays all floors inside that property.
**User clicks a floor**
-System shows all units on that floor.
-System displays:
-Total area of each unit
**Booked area**
-Available area
-Example:
--Unit 102: 1000 sq ft total | 500 booked | 500 available
-User clicks on a specific unit
-System opens the unit details page.
-System highlights remaining sq ft visually (bar/percentage).
-User enters how much space they want
**Example**:
-User enters 300 sq ft
**System validates the request**
-If requested area ≤ available area → system allows booking
-If requested area > available area → system blocks booking
**System message example**:
-Only 500 sq ft left. Please reduce your requested area.
-User confirms the booking
-System saves the booking.
-System recalculates remaining space immediately.
-System updates availability for everyone
**After the booking:**
-Available sq ft updates in MongoDB
-React UI updates the numbers instantly
**Color indicators refresh**:
-Green = Good availability
-Yellow = Limited
-Red = Almost full
-----


## *Multi-Property Booking & Bundled Offers*
**Feature**:Multi-Property Booking & Bundled Offers

**What the System Does**
-Allows users to book multiple units or properties in a single process.
-Automatically checks availability for all selected units.
-Applies bundled discounts if the user qualifies (e.g., booking 3+ units).
-Generates a combined booking summary with total rent, duration, and offers.
-Ensures no double-booking by locking units during checkout.
-How Users Interact With It
**User Actions**
-User browses properties and selects multiple units across floors or buildings.
-Adds the selected units to a Booking Cart (like e-commerce).
-Proceeds to Booking Summary.
-Views total rent, available bundle offers, and final price.
-Confirms and submits booking request.
**System Actions**
-Validates availability for each selected unit.
-If units are available → locks them temporarily during checkout.
-Checks if user qualifies for bundled discounts → automatically applies it.
**Generates a final invoice summary**.
-Sends booking confirmation with breakdown of units and discounts.
-Updates unit availability in real-time.
**Example Scenario**
-A company wants two separate office units (Unit 101 & Unit 204).
-They select both → system checks availability → applies a “Book 2 units = ₹3,000 off” offer.
-User gets a single combined booking summary → confirms → units are booked instantly.

----

##  *Follow & Availability Alerts for Properties*
**Feature**: Follow & Availability Alerts for Properties

**Following a Property**
-User does: Clicks the “Follow” button on a property that is currently unavailable.
-System does: Records the user-property relationship in MongoDB and stores the user’s alert preferences (email, WhatsApp, or in-app).
**Monitoring Property Availability**
-System does: Checks property availability daily or in real-time whenever a slot opens.
**Sending Alerts**
-System does: Sends automated notifications via:
-Email
-WhatsApp API
-In-app alerts
-User does: Receives the alert and can take action (e.g., book the property immediately).
**Optional Features**
-System does: Tracks which users have already been notified for a particular availability to avoid duplicate alerts.
-System does: Provides a dashboard for users to manage followed properties and alert preferences.
**Outcome:**
-Users never miss an opportunity on desired properties.
-Tenants are proactively engaged, increasing chances of occupancy.
-Admins can track interest levels in properties for better planning.

----


##  *Visit Booking with Conflict Detection*
**Feature**: Visit Booking with Conflict Detection

**Property Visit Selection**
-User does: Opens a property page and clicks “Book a Visit.”
-System does: Fetches available visit dates and displays them on an interactive calendar UI.
**Booking & Conflict Detection**
-User does: Selects a preferred date and submits the booking request.
-System does: Checks MongoDB for existing bookings for that property on the selected date.
-if the date is available, system confirms the booking.
-If the date is already booked, system automatically suggests alternative available dates.
**Confirmation & Notifications**
-System does: Updates the booking in the database.
-System does: Sends notifications to:
-Tenant: Confirms visit or suggests alternative dates.
-Admin / Property Owner: Notifies them of scheduled visits.
**Optional Features**
-System does: Allows rescheduling or canceling visits.
-System does: Prevents double-booking across multiple users automatically.

---


#  *Private Negotiation for Rent/Lease*
**Feature**: Private Negotiation for Rent/Lease

**Eligibility Check**
-System does: Determines whether the selected property/unit is marked as negotiable.
**Submitting a Negotiation Request**
-User does: Enters their proposed rent/lease amount and submits the negotiation form.
-System does: Saves the request securely in MongoDB with restricted visibility—only the tenant and property owner/admin can view it.
**Notification to Owner/Admin**
-System does: Sends an alert (email or in-app) to the property owner/admin about the new negotiation request.
**Owner/Admin Action**
-Owner/Admin does: Reviews the negotiation request and can:
-Accept the offer → lease terms updated automatically
-Reject the offer → tenant is notified
-Counteroffer → tenant receives a response to review and accept/reject
**Privacy & Security**
-System does: Ensures other tenants or users cannot see negotiation amounts.
-System does: Tracks negotiation history for audit purposes.
**Outcome:**
--Tenants can negotiate rent privately.
--Property owners/admins can review, approve, or counter offers securely.
--System maintains full privacy and proper record-keeping of all negotiations.

----



##  *Payments*
**Feature:** Track rent payments, generate receipts, highlight overdue payments, and send reminders.

**Explanation:**
Tenants can pay rent online and download receipts. Admins can track payments and monitor overdue amounts, ensuring smooth financial operations.

**Example Scenario:**
October rent not yet paid → the system highlights the overdue payment → sends automatic email reminder to tenant → admin dashboard reflects overdue status.

**Implementation:**
- Backend: MongoDB stores payment records.
- Frontend: Payment dashboard displaying history and status.
- Optional: Integration with payment gateways like Razorpay or Stripe.

---

## *Automated Tenant Management & Secure Document Storage*

**Tenant Registration via Payment**
-User does: Makes a payment for a property/unit using the system’s payment portal.
-System does: Verifies the payment and links it to the property/unit ID.
-System does: Automatically creates a tenant record in MongoDB with the user’s information and assigned unit(s).
**Document Upload & Storage**
-User does: Uploads required documents (ID proof, company registration, lease forms) via a secure form.
-System does: Stores documents in AWS S3 with restricted access.
-System does: Links documents to the automatically created tenant record.
**Tenant Access & Security**
-Tenant does: Logs in to view their assigned unit details, lease, and maintenance history.
-System does: Ensures that tenants only see their own information.
**Edit & Update Records**
-System does: Updates tenant records automatically if payments or leases are extended or modified.
-Admin does (optional): Can override or update tenant information if necessary.
**Notifications**
-System does: Sends automated notifications to tenants about:
-Lease confirmation
-Upcoming payments
-Uploaded or required documents

---




## *Maintenance Requests Management*
**Feature**: Maintenance Requests Management


**Submitting a Maintenance Request**
-Tenant does: Opens their unit dashboard and clicks “Submit Maintenance Request.”
-Tenant does: Fills in details (issue description, urgency, optional images) and submits.
-System does: Creates a maintenance ticket in MongoDB with status Pending and links it to the tenant and unit.
**Assignment & Processing**
-Manager/Admin does: Views the list of pending requests and assigns each task to maintenance staff.
-System does: Updates ticket status to In Progress and tracks assigned staff.
**Status Updates & Notifications**
-System does: Sends notifications to the tenant whenever the status changes:
-Pending → In Progress → Completed
=Tenant does: Receives updates in real-time via dashboard or email/SMS notifications.
**Completion & Feedback**
-Maintenance staff does: Marks the task as Completed after finishing the work.
-Tenant does: Can optionally provide feedback or confirm completion.
**Security & Access Control**
-System does: Ensures only authorized staff and managers can view and update tickets.
-System does: Tenants can only see their own maintenance requests.
**Outcome**:
-Provides efficient tracking and management of all maintenance issues.
-Keeps tenants informed in real-time.
-Ensures accountability and proper assignment of maintenance tasks.

--- 




##  *Notification & Alert System* 
**Feature**: Notification & Alert System

**Event Detection**
-System does: Monitors key events in the platform, such as:
-Lease expirations
-Upcoming or missed payments
-Maintenance request updates
-Visit bookings
-Property status changes (availability, new units, etc.)
**Notification Scheduling**
-System does: Uses cron jobs (scheduled tasks) in Node.js to check for upcoming events.
-System does: Stores notification status and history in MongoDB.
**User Alerts**
-Tenant / Admin / Owner does: Receives alerts via:
-In-app notification panel
-Optional email or SMS if enabled
-System does: Updates notifications in real-time whenever an event occurs.
**Notification Management**
-System does: Ensures users only see relevant alerts based on their role and property association.
-System does: Tracks read/unread status of notifications.
**Optional Features**
-System does: Groups similar alerts (e.g., multiple maintenance updates) for clarity.
-System does: Provides action buttons directly in notifications (e.g., “Pay Now,” “Confirm Visit”).
-Outcome:Keeps users informed in real-time.
-Prevents missed payments, scheduling conflicts, or overlooked maintenance.
-Enhances tenant engagement and admin efficiency.





## *Map Feature (React Simple Maps Version)*
**Feature**:Displaying Properties in maps 

**Showing Properties on a Map**
-System does:
-Loads all property coordinates (lat/lng) from MongoDB.
-Converts coordinates to map projection format (React Simple Maps uses geo projections).
-Displays markers on the map using <Marker> component.
-User does:
-Opens the map page.
-Sees all properties plotted on the map.
**Clicking a Property Marker**
-User does:
-Clicks on a marker for a property (example: Skyline Towers).
-System does:
-Opens a tooltip or popup above the marker showing:
-Property name
-Availability
-Short description
-“View Property” button
**Redirect to Property Page**
-User does:
-Clicks “View Property”.
-System does:
-Navigates to the full property page (/properties/:id).
**Extra Map Features**
-System does:
-Highlights available properties with green circles, unavailable with red.
-Shows hover tooltips with property name.
-Clusters nearby markers (optional, using custom logic).
-Provides zoom + pan controls.
---




## *Chatbot Feature*
**Feature**:Chatbot using NLU

**How the System Works**
--User opens the chatbot
--System greets the user and asks what they are looking for.

**Example message shown to the user**:
“Hello! What type of property do you need?”

**User sends a message**
-The user types something like:
-Show me office spaces near Anna Nagar with parking and a gym.”

**System understands the requirement**
-The AI analyzes the user’s message and identifies:
-Location preference
-Property type
-Required amenities
-Size (if mentioned)
-Budget (if mentioned)
-The system turns the user message into actual filters internally.
**System searches the database**
-The system automatically:
-Checks all properties
-Filters them based on user preferences
-Checks availability
-Collects details like price, size, amenities, floors, units
-Fetches images and floor plans

**System shows the best matches to the user**
-In the chat, the system displays a clean list of suitable properties.
Example response:
-Skyline Towers – Office space, Gym, Parking
-Green Heights – 2 units available, Near Anna Nagar
-Each property will have:
**Basic details**
-Availability
-Price
-Buttons to view more details
-User selects one property
-User types something like:
-Show me more about Skyline Towers.”
-System shows detailed information
**The system responds with**
-Property images
-Floor & unit availability
-Amenities
-Pricing
-Visit booking option
-Negotiation option (if available)
**System also asks:**
-Would you like to book a visit or negotiate the price?”
-User books a visit or negotiates
**User**:
-“Book a visit for Friday evening.”
or
-“I want to negotiate the price.”
**System handles the reques**
-Checks visit availability
-Blocks the slot
-Sends confirmation
-Sends notifications to admin/owner
-Saves user interest for future recommendations
-Additional System Behavior
-Saves user preferences (e.g., location, budget)
-Uses past searches to personalize results
-Suggests new properties when they become available
-Shows intelligent recommendations automatically
-Benefits
-Very easy for users to find the perfect property
-Reduces the need for manual browsing
-Makes the website feel modern, smart, and interactive
-Helps users who don’t understand filters or search
-Significantly improves user experience





## *Virtual 3D Tours / Interactive Floor Plans*

**Feature**: Virtual 3D Tours / Interactive Floor Plans
**What it does**:
Allows users to explore properties virtually in 3D or via interactive floor plans, seeing layouts, room sizes, and amenities without visiting physically.

**Example**:
Tenant selects Unit 102 → clicks “Virtual Tour” → an interactive 3D model opens with rotation, zoom, room navigation, and clickable hotspots for amenities.

**Implementation**:

-Backend: Node.js + MongoDB stores metadata; AWS S3 stores 3D model files.
-Frontend: React component using Three.js or Babylon.js to render models and hotspots.
**Implementation Steps** (Matterport)
-Scan the Property
-Use a Matterport camera or mobile app to capture the entire floor/property.
-Include all rooms, walls, doors, and amenities for a realistic 3D model.
-Generate Embed URL
-Matterport processes the scan and provides a shareable link or iframe embed code.
-Store in Backend
-Save the Matterport URL in MongoDB under the property’s record.
-Optional: Create an API endpoint to fetch the URL dynamically.
**Frontend Integration**
-Add a “Virtual Tour” button on the property page.
-On click, load the Matterport embed in the page for full interaction.
**User Interaction**
-Users can rotate, zoom, and move between rooms using mouse or touch.
-Clickable hotspots show amenities or room info.






## Implementation Flow Summary
1. Setup React frontend + Node.js backend
2. Setup MongoDB for all entities (users, properties, floors, units, tenants, leases, payments, negotiations, visit bookings, follows)
3. Setup AWS S3 for cloud storage
4. Implement authentication & role-based access
5. Build property → floor → unit → tenant pages
6. Build lease, payment, negotiation, visit booking, follow & alert, and filter management pages
7. Build maintenance request system
8. Build dashboards with charts
9. Implement AI features
10. Implement map feature with filters
11. Implement smart availability and partial unit booking
12. Test, debug, and deploy
