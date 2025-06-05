flowchart TD
    A[🚀 Inicio: Recolección de Datos SpaceX API] --> B[📋 Inicializar Listas Vacías]
    
    B --> C[PayloadMass = []]
    B --> D[Orbit = []]
    B --> E[Block = []]
    B --> F[ReusedCount = []]
    B --> G[Serial = []]
    B --> H[Outcome = []]
    B --> I[Flights = []]
    B --> J[GridFins = []]
    B --> K[Reused = []]
    B --> L[Legs = []]
    B --> M[LandingPad = []]
    
    C --> N[🔄 Función getPayloadData]
    D --> N
    E --> N
    F --> N
    G --> N
    H --> N
    I --> N
    J --> N
    K --> N
    L --> N
    M --> N
    
    N --> O[📡 Llamada API: /v4/payloads/]
    O --> P{¿Payload existe?}
    
    P -->|Sí| Q[📊 Extraer mass_kg del payload]
    P -->|No| R[❌ Asignar None a PayloadMass]
    
    Q --> S[📍 Extraer orbit del payload]
    R --> S
    S --> T[📂 Agregar datos a listas]
    
    T --> U[🔄 Función getCoreData]
    U --> V[📡 Llamada API: /v4/cores/]
    V --> W{¿Core existe?}
    
    W -->|Sí| X[🔧 Extraer datos del core:]
    W -->|No| Y[❌ Asignar None a campos]
    
    X --> X1[• Block Number]
    X --> X2[• Reuse Count]
    X --> X3[• Serial Number]
    X --> X4[• Flight Count]
    X --> X5[• Grid Fins Status]
    X --> X6[• Reused Status]
    X --> X7[• Legs Status]
    X --> X8[• Landing Pad]
    
    Y --> Y1[Block = None]
    Y --> Y2[ReusedCount = None]
    Y --> Y3[Serial = None]
    
    X1 --> Z[📊 Determinar Outcome del Aterrizaje]
    X2 --> Z
    X3 --> Z
    X4 --> Z
    X5 --> Z
    X6 --> Z
    X7 --> Z
    X8 --> Z
    Y1 --> Z
    Y2 --> Z
    Y3 --> Z
    
    Z --> AA{¿landing_success?}
    AA -->|True| BB[✅ Outcome = 'True']
    AA -->|False| CC[❌ Outcome = 'False']
    AA -->|None| DD[❓ Outcome = 'None']
    
    BB --> EE[📈 Agregar todos los datos a listas]
    CC --> EE
    DD --> EE
    
    EE --> FF[🌐 Solicitar datos de lanzamientos]
    FF --> GG[📡 GET: api.spacexdata.com/v4/launches/past]
    GG --> HH[📋 Procesar respuesta JSON]
    
    HH --> II{¿Más lanzamientos<br/>por procesar?}
    II -->|Sí| N
    II -->|No| JJ[✅ Datos recolectados exitosamente]
    
    JJ --> KK[📊 Dataset completo con:]
    KK --> LL[• Masa del payload]
    KK --> MM[• Órbita de destino]
    KK --> NN[• Características del core]
    KK --> OO[• Resultados de aterrizaje]
    
    LL --> PP[🎯 Datos listos para análisis]
    MM --> PP
    NN --> PP
    OO --> PP
    
    style A fill:#ff9999
    style PP fill:#99ff99
    style O fill:#ffcc99
    style V fill:#ffcc99
    style GG fill:#ffcc99
    style AA fill:#ccccff
    style P fill:#ccccff
    style W fill:#ccccff
