# 5G Technology, Architecture And Protocols

## Table of Contents
- [Introduction](#introduction)
- [5G Network Architecture](#5g-network-architecture)
- [Identifiers in 5G](#identifiers-in-5g)
- [Procedures in 5G Networks](#procedures-in-5g-networks)
- [Service Based Architecture](#service-based-architecture)
- [UE State Management in 5G](#ue-state-management-in-5g)

---

## Introduction

### 1. Evolution to 5G

Mobile network technology has evolved significantly over the years:

| Generation | Technology | Speed |
|---|---|---|
| 2.5G | GSM/GPRS | 50 Kbps |
| 2.75G | EDGE | 150 Kbps |
| 3G | UMTS | 384 Kbps |
| 3.5G | UMTS/HSPA | 10 Mbps |
| 3.75G | UMTS/HSPA+ | 20 Mbps |
| 4G | LTE | 20–50 Mbps |
| 4.5G | LTE Advanced | 1 Gbps+ (Low 100 Mbps) |
| **5G** | **NR** | **20 Gbps (High hundreds of Mbps)** |

---

### 2. Standardization of 5G

- **ITU-R** (International Telecommunication Union – Radiocommunication) is responsible for developing 5G requirements

| Year | Standard | Generation |
|---|---|---|
| 2000 | IMT 2000 | 3G |
| 2008 | IMT Advanced | 4G |
| 2015 | IMT 2020 | 5G |

- Technical specifications are developed by **3GPP** (Third Generation Partnership Project)
- 3GPP is a consortium of major Telecom Vendors and Operators
- Vendors manufacture equipment according to 3GPP specifications

---

### 3. ITU-R Minimal Technical Requirements for IMT-2020

> Reference: **3GPP TR 38.913** | Diagram: ITU-R Recommendation M.2083

| Parameter | Requirement |
|---|---|
| Peak Data Rate | 20 Gbps |
| User Experienced Data Rate | 100–1000 Mbps |
| Spectrum Efficiency | 3x improvement |
| Mobility | Up to 500 km/h |
| Latency | 1 ms |
| Connection Density | 10⁶ devices/km² |
| Network Energy Efficiency | 100x improvement |
| Area Traffic Capacity | 10 Mbps/m² |

---

### 4. IMT Use Cases — Usage Scenarios

5G supports **3 main usage scenarios:**

#### 4.1 Enhanced Mobile Broadband (eMBB)
- **Main driver** for 5G development
- High importance on: Peak Data Rate, User Experienced Data Rate
- **Applications:**
  - 3D Video
  - UHD Video Streaming
  - Work and play in the cloud
  - Augmented Reality

#### 4.2 Massive Machine Type Communications (mMTC)
- Large number of connected devices
- Long battery life
- High connection density
- **Applications:**
  - Internet of Things (IoT)
  - Smart Home / Smart City

#### 4.3 Ultra-Reliable and Low Latency Communications (uRLLC)
- Extremely low latency with high reliability
- High importance on: **Latency**, Connection Density
- **Applications:**
  - Industrial Automation
  - Remote Surgery
  - Self-driving Cars
  - Mission Critical Applications

---

### 5. 5G Standardization Roadmap

- **3GPP** is the main standardization body for 5G

| Phase | Release | Details |
|---|---|---|
| 5G Study | Release 14 | Research & feasibility |
| 5G Phase 1 | Release 15 | Does **not** meet all IMT-2020 requirements |
| 5G Phase 2 | Release 16 | Frozen in March 2020, meets full IMT-2020 requirements |

```
Timeline:
|-- Release 14 --|-- Release 15 --|-- Release 16 --|
               Jun'17           Sep'18           Mar'20
            (5G Study)       (5G Phase 1)     (5G Phase 2)
```

**Summary:**
5G (IMT-2020) is not just faster mobile internet — it is designed to support three very different use cases:
- **eMBB** → High speed broadband
- **mMTC** → Massive IoT connectivity
- **uRLLC** → Mission critical, ultra-low latency applications

These are standardized by **ITU-R** (requirements) and **3GPP** (technical specs), with full deployment targeted through Release 16.

---

## 5G Network Architecture

### 1. 5G Architecture — gNB (Next Generation NodeB)

gNB (Next Generation NodeB) is the base station in 5G (NG-RAN).

**Functions of gNB:**
- Radio Resource Management
- Communication with Core Network and nearby base stations
- Radio Transmission / Reception
- Digital Signal Processing (encryption, data compression)
- Process Access Stratum (AS) Signaling
- Relay Non-Access Stratum (NAS) signaling to Core

---

### 2. PDU (Protocol Data Unit) Sessions

- 5G is an **all IP system**
- 5G provides data connectivity to UE as **PDU sessions**
- **QoS (Quality of Service)** is characterised by:
  - **Data Rate** — Guaranteed or Non-Guaranteed
  - **Latency**
  - **Priority**
- A single PDU Session can carry multiple **QoS flows** (QoS flow 1, QoS flow 2...)

---

### 3. Control and User Plane Separation in 5G

**Control Plane Functions:**
- Authentication
- Connection Management
- QoS Management
- Mobility Management

**User Plane Functions:**
- Data traffic forwarding

**Advantage: Scalability**
- More nodes can be added to handle data traffic independently

**Key Network Functions:**

| Function | Type | Role |
|---|---|---|
| AMF | Control Plane | Access & Mobility Management |
| SMF | Control Plane | Session Management |
| PCF | Control Plane | Policy Control |
| AF | Control Plane | Application Function |
| AUSF | Control Plane | Authentication |
| UDM | Control Plane | User Data Management |
| UDR | Control Plane | User Data Repository |
| UPF | **User Plane** | User Plane Function (data forwarding) |
| gNB | RAN | Base Station |

---

## Identifiers in 5G

### 1. 5G UE Identifiers (Permanent)

UE (User Equipment) = Device + SIM card

**Device Identifiers:**

| Identifier | Full Form | Details |
|---|---|---|
| **PEI** | Permanent Equipment Identity | Identifies the device hardware, currently only supported format is IMEI |

**SIM / Subscription Identifiers:**

| Identifier | Full Form | Details |
|---|---|---|
| **SUPI** | Subscription Permanent Identifier | Can be either IMSI or NAI (for non-3GPP access) |
| **SUCI** | Subscription Concealed Identifier | SUPI encrypted by public key (for privacy protection) |

---

### 2. 5G UE Identifiers (Temporary)

Temporary identifiers assigned by the network to protect UE identity:

| Identifier | Full Form | Details |
|---|---|---|
| **5G-S-TMSI** | 5G S Temporary Mobile Subscriber Identity | Assigned by AMF, unique within AMF region |
| **5G-GUTI** | 5G Globally Unique Temporary Identifier | Assigned by AMF, used when AMF region of UE is not known |

---

### 3. Tracking Areas in 5G

- A mobile network is divided into **Tracking Areas (TA)**
- Tracking areas do **not overlap**
- In **Idle mode**, the TA of a UE is always known to the network

**In case of incoming call:**
- All UEs in the TA need to be paged with **5G-S-TMSI**
- **TA update** happens when a mobile enters a cell with a different TA

**TA List:**
- Core network can assign UE a specific **TAs list**
- UE can roam within those TAs **without TA update**

---

### 4. 5G Network Identifiers

| Identifier | Full Form | Formula |
|---|---|---|
| **PLMN-ID** | Public Land Mobile Network Identity | MCC \| MNC |
| **AMI** | AMF Identifier | Unique ID for AMF |
| **GUAMI** | Globally Unique AMF Identifier | MCC \| MNC \| AMI |
| **TAI** | Tracking Area Identity | MCC \| MNC \| TAC |

> **MCC** = Mobile Country Code | **MNC** = Mobile Network Code | **TAC** = Tracking Area Code

**Summary:**

| Category | Identifiers |
|---|---|
| UE Permanent | PEI, SUPI, SUCI |
| UE Temporary | 5G-S-TMSI, 5G-GUTI |
| Network | PLMN-ID, GUAMI, TAI |

---

## Procedures in 5G Networks

### 1. UE Power-On Procedure

When a UE (device) powers on, it goes through the following steps:

**Overall Flow:**
1. Cell Acquisition → Network Selection → Cell Selection
2. Radio Connection
3. Registration (with 5GC)

#### 1.1 Cell Acquisition

- UE discovers nearby cells by reading their **PSS** (Primary Synchronization Signal) and **SSS** (Secondary Synchronization Signal)
- If it is a **primary cell** → cell broadcasts system information on **PBCH** (Physical Broadcast Channel) which describes cell configuration and PLMN-ID
- If **no system information** → the cell is ignored

#### 1.2 Network Selection (Cell Acquisition Phase)

- UE discovers nearby cells by decoding their **broadcast channels**
- Broadcast channel carries the cell **PLMN-ID**

#### 1.3 Network Selection

UE selects network in this priority order:
1. Last registered PLMN (if available)
2. Else → Home PLMN-ID
3. PLMN on user list
4. PLMN operator list
5. Cell with most powerful PLMN-ID

#### 1.4 Cell Selection

- UE goes to the **best cell** in the selected PLMN network

#### 1.5 Establish Security

- Security based on **5G AKA** (Authentication and Key Agreement)
- AKA relies on a **shared secret key**:
  - USIM stores one copy
  - UDM stores the other
- Secret key used for **mutual authentication** — both the device and the network authenticate each other
- All signalling between device and network is encrypted:
  - UE ↔ AMF (signalling encrypted)
  - UE ↔ gNB (signalling + data encrypted)

#### 1.6 UE Context Installation

- Every valid subscriber has a **subscriber profile** stored in the **UDM**
- AMF sends **UE Context query** to UDM → UDM returns **UE Context Provision**
- This profile defines:
  - Allowed DN connections
  - QoS
  - Bandwidth
  - Roaming
  - Subscriber status

#### 1.7 UE Policy Check

- AMF performs a **policy check** with the **PCF**
- Policy decisions influenced by:
  - Time of day
  - Location of the user
  - Network congestion
- Policy check determines if subscriber can access the network under current conditions

#### 1.8 5G-S-TMSI Allocation

- Finally, a **temporary ID** is allocated to the subscriber
- **5G-S-TMSI** is created by the **AMF**
- Used until the device is re-allocated a new one — potentially due to an AMF change

---

### 2. UE Idle and Connected Modes

#### Idle Mode
- UE location known to **TA (Tracking Area) level**
- UE is **camping** on a cell
- UE listens to paging
- UE paged using **5G-S-TMSI**

#### Connected Mode
- UE is actively exchanging voice or data with the network
- **5G-S-TMSI** used for communication
- UE location known to **cell level**

---

### 3. PDU Session Establishment

**Steps:**
1. UE sends **PDU Session Establishment Request** → AMF
2. SMF performs **Policy Check** → PCF
3. PCF sends **Policy Decision** → SMF
4. SMF co-ordinates with AMF and UPF to establish user data PDU session
5. **PDU session established**

---

### 4. Paging Procedure

**Steps:**
1. Downlink data arrives at **UPF**
2. UPF notifies **SMF** about incoming data
3. SMF asks **AMF** to page the UE
4. AMF pages **all UEs in the tracking area**

---

### 5. Tracking Area Update Procedure

**Steps:**
1. UE enters a cell with a **different TA** → TA update initiated
2. UE sends **TA Update Request** → AMF
3. AMF **deletes old TA** and records the new one
4. AMF **notifies UE** about TA update

---

### 6. Handovers in 5G

- Handovers always take place when **UE is in Connected state** during a call
- The **network decides** when a device switches from one cell to the next
- Two mechanisms of handover in 5G:
  - **Xn Handover**
  - **N2 Handover**

#### 6.1 Xn Handover (Direct between gNBs)

**Steps:**
1. **Handover Co-ordination** between source and target gNB (Security info + PDU session info exchanged)
2. Device connected to new cell
3. Request to switch PDU session → SMF
4. Request to switch PDU session → UPF
5. **New PDU Session path established**

#### 6.2 N2 Handover (Via AMF)

**Steps:**
1. **Handover Co-ordination** → AMF
2. Device connected to new cell
3. Request to switch PDU session → SMF → UPF
4. **New PDU Session path established**

**Summary:**

| Procedure | Key Network Functions Involved |
|---|---|
| Power-On | NG-RAN, AMF, UDM, PCF, AUSF |
| PDU Session Establishment | AMF, SMF, PCF, UPF |
| Paging | UPF, SMF, AMF |
| TA Update | AMF |
| Xn Handover | gNB-gNB, SMF, UPF |
| N2 Handover | AMF, SMF, UPF |

---


## Service Based Architecture

### 1. 5G Service Based Architecture (SBA)

- Service Based Architecture introduced to increase **modularity**
- A **"Network Function"** provides one or more services to other Network Functions in the network
- These services are made available over **Service Based Interfaces (SBI)** of Network Function interfaces

---

### 2. 5G Service Based Vs Reference Point Architecture

Two ways to represent the same 5G Core architecture:

| Architecture | Description |
|---|---|
| **Service Based Architecture** | NFs expose services via SBI (e.g., Namf, Nsmf, Nnrf) |
| **Reference Point Architecture** | NFs connected via defined reference points (e.g., N1, N2, N3, N4...) |

**Key Network Functions:**

| NF | Service Based Interface |
|---|---|
| AMF | Namf |
| SMF | Nsmf |
| NRF | Nnrf |
| UDM | Nudm |
| PCF | Npcf |
| AUSF | Nausf |
| NEF | Nnef |
| AF | Naf |

---

### 3. Main Mechanisms for NF Services

#### Request-Response
- NF service consumer **requests** a service
- NF service provider **returns**:
  - Information to the consumer, or
  - Performs an action, or both

#### Subscribe-Notify
- NF service consumer **subscribes** to provider's service
- Provider **notifies** the consumer about:
  - The occurrence of events, or
  - Periodic updates related to the service

---

### 4. HTTP/2 for 5G Core Network

- **HTTP/2** used for communication between NFs
- Easy deployment in **cloud environment**
- HTTP/2 is already very widely deployed:
  - Well developed security mechanisms
  - Well developed third party applications
- Easy integration of **operator and third-party applications**

**HTTP/2 on Web vs HTTP/2 in 5G Core:**

| | Internet (Web) | 5G Core |
|---|---|---|
| Request | HTTP Request with possible content | HTTP Request with possible JSON content |
| Response | HTML, JPG, PDF | JSON content |

---

### 5. JSON (JavaScript Object Notation) Format

- JSON uses **name-value pairs** to represent data
- Used as the message body format in 5G Core HTTP/2 communications

**Example:**
```json
{
  "empid": "SJ011MS",
  "personal": {
    "name": "Smith Jones",
    "gender": "Male",
    "age": 28,
    "address": {
      "streetaddress": "7 24th Street",
      "city": "New York",
      "state": "NY",
      "postalcode": "10038"
    }
  },
  "profile": {
    "designation": "Deputy General",
    "department": "Finance"
  }
}
```

---

### 6. Concept of Resource in 5G SBA

- Resources are located and manipulated as **URI (Uniform Resource Identifier)**
- NF sends **HTTP Request to URI** → NF responds with **HTTP Response**

**Examples of Resources:**
- PDU Session → context, QoS Policy
- NF registration with NRF

---

### 7. HTTP Methods used in 5GC

| Method | Description |
|---|---|
| **PUT** | Create or Replace a resource |
| **GET** | Read a resource (no modification) |
| **PATCH** | Partially update a resource |
| **DELETE** | Delete a resource |
| **POST** | Create a resource / Process enclosed information / Execute a remote call |

---

### 8. HTTP Responses in 5G

Responses defined by **three digit code:**

| Code Range | Type | Examples |
|---|---|---|
| **2xx** | Success | 200 OK, 201 Created, 202 Accepted |
| **4xx** | Client Error | 400 Bad Request, 404 Not Found |
| **5xx** | Server Error | 500 Internal Server Error, 503 Server Unreachable |

---

### 9. Naming Scheme for NF Services

Format: **`Nnfname_ServiceName_ServiceOperation Method`**

| Part | Meaning |
|---|---|
| **Nnfname** | Service Based Interface used to provide the service |
| **ServiceName** | Name of Service (API) |
| **ServiceOperation** | Type of operation |
| **Method** | How service operation is used |

**Examples:**
- `Nsmf_PDUSession_Create Request`
- `Nsmf_PDUSession_Create Response`

---

### 10. REST Applied to 5G Services

- **REST** (Representational State Transfer) — an architectural style for softwares
- Defines a set of rules for design of distributed applications
- The **5GC service APIs** are implemented according to the REST paradigm
- In the context of 5GC, rules of REST applied to **HTTP protocol**

**Principles of RESTful Design:**

| Principle | Description |
|---|---|
| **Client/Server** | Split of responsibilities between client and server |
| **Stateless** | Each request must contain all information necessary; session state kept entirely on client |
| **Cacheable** | Clients get indication from servers whether received information can be cached |
| **Uniform Interface** | Identification and manipulation of resources through URIs |
| **Layered System** | Each component cannot "see" beyond the immediate layer it is interacting with |

---

### 11. Use Case 1 — Network Function Service Registration

NF registers itself with the **NRF** so other NFs can discover it.

**Registration Request — HTTP PUT:**
```
HTTP PUT to the URI {apiRoot}/{apiName}/{apiVersion}/nf-instances/{nfInstanceID}
```

**ApiRoot details:**
- Scheme: `HTTP://` or `HTTPS://`
- Host name: `nrf.5gc.mnc015.mcc234.3gppnetwork.org`
- Optional port number
- ApiName: `nnrf-nfm`
- ApiVersion: `v1`
- NfInstanceID: Unique ID

**JSON Message Body (NFRegister Request) contains:**
- **nfInstanceID** — unique identity of NF instance
- **nfType** — e.g., 'NRF', 'UDM', 'AMF', 'SMF'
- **nfStatus** — 'REGISTERED' or 'SUSPENDED'
- **sNssais** — network slices that NF supports
- **capacity** — static capacity of NF
- **load** — %age dynamic load on NF
- IP address or domain name of NF

**Registration Response:**
- **HTTP 201 Created**
- JSON Message Body contains **heartbeat timer** (maximum number of seconds between heartbeat requests from the network function)

**NF Update — HTTP PATCH:**
```
HTTP PATCH to the URI {apiRoot}/{apiName}/{apiVersion}/nf-instances/{nfInstanceID}
```
- Response: **HTTP 200 OK**

---

### 12. Use Case 2 — NF Service Discovery

NF discovers other NFs by querying the **NRF**.

**Flow:**
1. Requester NF sends `Nnrf_NFDiscovery_NFDiscover Request` → NRF in serving PLMN
2. NRF in serving PLMN forwards request → NRF in target PLMN
3. NRF in target PLMN responds → NRF in serving PLMN
4. NRF in serving PLMN responds → Requester NF

**HTTP Method used:**
```
HTTP GET to the URI {apiRoot}/{apiName}/{apiVersion}/nf-instances/?<query parameters>
```

**Query Parameters:**
- service-names
- target-nf-type
- target-plmn
- requester-plmn
- Snssais: network slices supported by target services

**Response — HTTP 200 OK with JSON Body:**
- **ValidityPeriod**
- **NfInstances** (array of NFProfile)

---

## UE State Management in 5G

### 1. Introduction to UE State Management

- 5G System needs to keep track of each UE's:
  - **Availability**
  - **Reachability**
- Keeps track of **three states** of UE:
  - Radio Resource Control **(RRC)**
  - Connection Management **(CM)**
  - Registration Management **(RM)**

---

### 2. Radio Resource Control (RRC) State

Represents the **status of RRC connection between UE and gNB.**

#### RRC-Idle
- No RRC connection
- UE monitors broadcast info
- Cell selection / reselection

#### RRC-Connected
- Active RRC connection exists
- UE location known to **cell level**
- RRC connection required for:
  - Registration
  - Voice Call etc.

#### RRC-Inactive *(New in 5G)*
- Intermediate state introduced in 5G
- RRC connection context (parameters) stored
- RRC connection can be activated with **minimum signalling**
- Decrease in signalling overhead
- Suitable for **Massive IoT**

**RRC State Transitions:**

```
RRC-Idle  <──────────────────────────  RRC-Connected
   │          RRC Connection Release        │
   │                                        │
   └──────────────────────────────────>  RRC-Connected
        RRC Connection Establish            │
                                     RRC Connection Suspend
                                            │
                                            ▼
                                      RRC-Inactive
                                            │
                                     RRC Connection Resume
                                            │
                                            ▼
                                      RRC-Connected
```

---

### 3. UE Mobility in RRC_Inactive State — RAN Areas

- **RAN areas** are very like Tracking Areas (TAs), but relevant to the RAN
- **Size of RAN area:**
  - Minimum → one cell of a TA
  - Maximum → all the cells of a TA
- RAN areas do **not overlap**
- Each RAN area is identified using a **RAN area ID**

---

### 4. UE Mobility in RRC_Inactive — RAN-based Notification Areas (RNAs)

- One or more RAN areas of same TA can be grouped as **RNA**
- The 5G RAN can assign a RNA to a UE
- In **RRC_INACTIVE** state:
  - The RAN knows the RNA in which mobile is in
  - RNA notifies the network if it moves to another RNA
  - To contact UE, RAN pages all the cells in a RNA
- **Reduced Signaling:** RNA updates instead of cell updates

---

### 5. Connection Management (CM) State

Represents whether an **active NAS connection exists between UE and AMF** or not.
- Also called **N1 signalling link**
- UE TA list = Registration Area

| State | Description |
|---|---|
| **CM-Idle** | No N1 connection; UE Registration Area known to AMF |
| **CM-Connected** | Active N1 connection; AMF knows UE's current gNB |

**CM-Connected used for:**
- Registration
- Data transfer
- Registration Update

**CM State Transitions:**
```
CM-Idle  ──── RRC Connection Established ────>  CM-Connected
CM-Idle  <─── RRC Connection Released    ─────  CM-Connected
```

---

### 6. Registration Management (RM) State

Represents whether the **UE is registered with the 5G Core or not.**

| State | Description |
|---|---|
| **RM-Deregistered** | UE switched off or deregistered |
| **RM-Registered** | UE registered with 5GC, served by an AMF, assigned a 5G-GUTI |

**RM-Registered details:**
- Registered with 5GC
- Served by an AMF
- Assigned a **5G-GUTI**
- Registration update when UE enters another RA (Registration Area)

**RM State Transitions:**
```
RM-Deregistered  ──── Registration ────>  RM-Registered
RM-Deregistered  <─── Deregistration ───  RM-Registered
```

---

### 7. Combined State Diagram

The three state machines (RRC, CM, RM) work together:

| Combined State | RRC State | CM State | RM State |
|---|---|---|---|
| UE Power UP → | RRC-IDLE | CM-IDLE | RM-Deregistered |
| After Registration → | RRC-IDLE | CM-IDLE | RM-Registered |
| Active Connection → | RRC-Connected | CM-Connected | RM-Registered |
| Inactive (5G new) → | RRC-INACTIVE | CM-Connected | RM-Registered |

**RM-Registered + CM-Connected (RRC-Connected):**
- Cell location known
- Handovers possible
- PDU sessions active

**RM-Registered + CM-Connected (RRC-Inactive):**
- RNA Update
- Cell Selection
- RAN Paging
- RRC connection can be activated with little signaling

**RM-Deregistered / RM-Registered + CM-IDLE (RRC-IDLE):**
- Cell selection / reselection
- No RRC signalling connection

---

### Summary

| State Type | States | Managed By |
|---|---|---|
| **RRC** | Idle, Inactive, Connected | gNB |
| **CM** | Idle, Connected | AMF (N1 link) |
| **RM** | Deregistered, Registered | AMF |
