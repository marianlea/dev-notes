# Dev Notes for Hablon

## Vendor Filtering Strategy

#### Purpose

> Ensure that only vendors with at least 1 active product are searchable and visible to buyers on the platform.

#### 1️⃣ Filtering Responsibility (Architecture Responsibility)

> - Where? → Backend (API/Database level)
> - Why?
>   > - Prevent exposure of incomplete or inactive vendors
>   > - Improves security, performance, and scalability
>   >   > - reduces data being sent to over the network
>   >   > - faster load times, smaller payloads
>   >   > - as the app grows, _pagination, search, filters, sorting_ all should be in backend responsibilities
>   > - Keeps frontend logic clean and focused on presentation or UI
>   >   > - frontend filtering works only for small, toy datasets

#### 2️⃣ API Design

> Example **GET request** for fetchcing vendors:

    GET /vendors?status=active&hasProducts=true

> **Backend filters vendors where:**
>
> > - status = 'active'
> > - numberOfProducts >= 1

#### 3️⃣ Frontend Responsbility

> - Fetches already-filtered data
> - Handles UI-level filters only (e.g., by product category, by region, by rating, etc.)

    const [vendors, setVendors] = useState([]);
    const [regionFilter, setRegionFilter] = useState('');

    const filteredVendors = vendors.filter(vendor =>
      regionFilter ? vendor.region === regionFilter : true
    );
