import React, { useState, useMemo, useEffect } from 'react';
import { 
  Users, 
  Search, 
  Plus, 
  AlertTriangle, 
  X, 
  Printer, 
  Trash2, 
  FolderOpen, 
  Building2, 
  Hammer, 
  Info, 
  Layers, 
  Heart, 
  QrCode, 
  ExternalLink, 
  Maximize2, 
  Cloud, 
  CloudOff, 
  Mail, 
  Send, 
  MapPin, 
  Clock, 
  Truck, 
  CheckSquare, 
  Square,
  ArrowLeft,
  Save,
  FileText
} from 'lucide-react';

import { initializeApp } from 'firebase/app';
import { 
  getAuth, 
  signInWithCustomToken, 
  signInAnonymously 
} from 'firebase/auth';
import { 
  getFirestore, 
  collection, 
  doc, 
  setDoc, 
  onSnapshot, 
  updateDoc, 
  deleteDoc 
} from 'firebase/firestore';

const fallbackFirebaseConfig = {
  apiKey: "AIzaSyFakePlaceholderKey_ReplaceWithYourActualKey",
  authDomain: "cromer-gowards-mortuary.firebaseapp.com",
  projectId: "cromer-gowards-mortuary",
  storageBucket: "cromer-gowards-mortuary.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef123456"
};

const firebaseConfig = typeof __firebase_config !== 'undefined' 
  ? JSON.parse(__firebase_config) 
  : fallbackFirebaseConfig;

const appId = typeof __app_id !== 'undefined' ? __app_id : 'cromer-gowards-mortuary';

const firebaseApp = initializeApp(firebaseConfig);
const auth = getAuth(firebaseApp);
const db = getFirestore(firebaseApp);

// Local Norfolk Staff directory with verified emails
const norfolkStaffList = [
  { id: "staff-1", name: "David (Cromer)", email: "david@cromerfunerals.co.uk" },
  { id: "staff-2", name: "Sarah (Cromer)", email: "sarah@cromerfunerals.co.uk" },
  { id: "staff-3", name: "Paul (Fakenham)", email: "paul@gowardsfunerals.co.uk" },
  { id: "staff-4", name: "Luke (Fakenham)", email: "luke@gowardsfunerals.co.uk" },
  { id: "staff-5", name: "Mark (Group Operations)", email: "mark@norfolkfuneralgroup.co.uk" }
];

const initialCaseload = [
  {
    id: "1",
    ref: "26/C/015",
    fridgeTray: "66A",
    keyDate: "26/06/2026",
    deceasedName: "Dennis Harrison",
    title: "Mr",
    dob: "14/10/1941",
    dod: "06/06/2026",
    arranger: "SCO",
    location: "Cromer",
    greenCoroner: "Yes",
    encoffined: "Yes",
    plate: "Yes",
    bodySize: "5'8\" x 20\"",
    condition: "Good",
    infection: "None",
    coffin: "Chiltern Oak",
    clothes: "White Funeral Gown",
    clothesChecked: true,
    preparations: "Yes",
    preparationsDetails: "Dignified presentation. Shave and hair parted to the left.",
    jewellery: "Yes",
    jewelleryDetails: "Gold wedding band to remain on left hand.",
    devices: "No",
    devicesDetails: "None",
    embalming: "Yes",
    embalmingDetails: "Completed on 08/06/2026",
    coffinAccessories: "Brass Handles",
    viewing: "Yes", 
    ready: "Yes",
    isCoroner: true,
    coronerRef: "CR-2026-881",
    coronerOfficer: "Officer J. Miller",
    pickupLocation: "Norfolk & Norwich University Hospital (NNUH)",
    pickupDestination: "Cromer Mortuary",
    pickupDateTime: "27/06/2026 10:00",
    pickupStaff: ["David (Cromer)", "Sarah (Cromer)"],
    pickupStaffEmails: "david@cromerfunerals.co.uk, sarah@cromerfunerals.co.uk",
    pickupVehicle: "Vauxhall Vivaro CRM-1",
    pickupEquipment: ["First Call Stretcher", "Body Bag"],
    pickupStatus: "Dispatched",
    pickupStatusTimestamps: {
      "Pending": "26/06/2026 09:15",
      "Dispatched": "26/06/2026 10:00"
    },
    pickupInstructions: "Collect from Pathology entrance B. Bring identity collar tag.",
    isArchived: false
  },
  {
    id: "7",
    ref: "26/C/005",
    fridgeTray: "1A",
    keyDate: "01/07/2026",
    deceasedName: "Elaine Bailey",
    title: "Mrs",
    dob: "08/07/1955",
    dod: "31/05/2026",
    arranger: "NEC",
    location: "Fakenham",
    greenCoroner: "No",
    encoffined: "No",
    plate: "No",
    bodySize: "5'6\" x 30\"",
    condition: "Poor",
    infection: "Blood borne",
    coffin: "Chiltern Oak",
    clothes: "Shroud Only",
    clothesChecked: false,
    preparations: "Yes",
    preparationsDetails: "Universal infection precautions strictly applied.",
    jewellery: "Yes",
    jewelleryDetails: "To be returned to family prior to cremation.",
    devices: "Yes",
    devicesDetails: "Pacemaker - requires removal",
    embalming: "No",
    embalmingDetails: "Declined due to infectious risks.",
    coffinAccessories: "Simple Coffin lining",
    viewing: "No", 
    ready: "No",
    isCoroner: false,
    coronerRef: "",
    coronerOfficer: "",
    pickupLocation: "",
    pickupDestination: "",
    pickupDateTime: "",
    pickupStaff: [],
    pickupStaffEmails: "",
    pickupVehicle: "",
    pickupEquipment: [],
    pickupStatus: "Pending",
    pickupInstructions: "",
    isArchived: false
  }
];

// Helper to generate current timestamp in clean DD/MM/YYYY HH:MM format
const getTimestamp = () => {
  const now = new Date();
  const dd = String(now.getDate()).padStart(2, '0');
  const mm = String(now.getMonth() + 1).padStart(2, '0');
  const yyyy = now.getFullYear();
  const hh = String(now.getHours()).padStart(2, '0');
  const min = String(now.getMinutes()).padStart(2, '0');
  return `${dd}/${mm}/${yyyy} ${hh}:${min}`;
};

export default function App() {
  const [deceasedList, setDeceasedList] = useState(initialCaseload);
  const [selectedRowId, setSelectedRowId] = useState(null); 
  const [isAuth, setIsAuth] = useState(false);
  const [activeTab, setActiveTab] = useState("care");
  const [activeBrand, setActiveBrand] = useState("joint");
  const [searchQuery, setSearchQuery] = useState("");
  const [locationFilter, setLocationFilter] = useState("All");
  const [statusFilter, setStatusFilter] = useState("Active"); // 'Active' or 'Archived'
  const [isQrModalOpen, setIsQrModalOpen] = useState(false);
  const [isEmailModalOpen, setIsEmailModalOpen] = useState(false);
  const [dialog, setDialog] = useState({ isOpen: false, title: "", message: "", type: "info", onConfirm: null });

  const locations = useMemo(() => ["Cromer", "Fakenham"], []);
  const officeShorthands = useMemo(() => ["SCO", "NEC", "ERD", "CRM", "FAK"], []);
  const conditions = useMemo(() => ["Good", "Medium", "Poor"], []);
  const infectionRisks = useMemo(() => ["None", "Blood borne", "Sepsis", "CJD", "Other"], []);
  const triStateOptions = useMemo(() => ["Yes", "No", "N/A"], []);
  const coffinsList = useMemo(() => ["Chiltern Oak", "Regent Oak", "New Ascot", "Simple coffin", "Mendip Oak", "Cardboard", "Simple Pine", "None"], []);
  const titles = useMemo(() => ["Mr", "Mrs", "Miss", "Ms", "Dr", "Rev", "Sir", "Lady"], []);
  const equipmentOptions = useMemo(() => ["First Call Stretcher", "Scoop Stretcher", "Body Bag", "Heavy Lift Gear", "PPE Kits"], []);
  const vehicleOptions = useMemo(() => ["Vauxhall Vivaro CRM-1", "Vauxhall Vivaro FAK-2", "Ford Transit Group-1", "First Call Vehicle 3"], []);

  useEffect(() => {
    const initAuth = async () => {
      try {
        if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
          await signInWithCustomToken(auth, __initial_auth_token);
        } else {
          await signInAnonymously(auth);
        }
        setIsAuth(true);
      } catch (error) {
        console.error("Firebase Auth failed:", error);
      }
    };
    initAuth();
  }, []);

  useEffect(() => {
    if (!isAuth) return;
    const caseloadCol = collection(db, 'artifacts', appId, 'public', 'data', 'caseload');
    const unsubscribe = onSnapshot(caseloadCol, 
      (snapshot) => {
        const items = [];
        snapshot.forEach((doc) => items.push({ id: doc.id, ...doc.data() }));
        if (items.length > 0) {
          setDeceasedList(items);
        }
      },
      (error) => console.error("Firestore read connection failed:", error)
    );
    return () => unsubscribe();
  }, [isAuth]);

  const selectedRecord = useMemo(() => {
    if (!selectedRowId) return null;
    return deceasedList.find(d => d.id === selectedRowId) || null;
  }, [deceasedList, selectedRowId]);

  useEffect(() => {
    if (selectedRecord && !selectedRecord.isCoroner && activeTab === 'pickup') {
      setActiveTab('care');
    }
  }, [selectedRecord, activeTab]);

  const brandThemes = useMemo(() => ({
    joint: {
      bannerGradient: 'from-slate-900 via-slate-950 to-slate-900',
      brandName: 'Cromer & District & Gowards Group',
      primaryBtn: 'bg-slate-800 hover:bg-slate-700 text-slate-200',
      activeTabStyle: 'border-amber-500 text-amber-400 bg-amber-950/20'
    },
    cromer: {
      bannerGradient: 'from-rose-950 via-slate-950 to-rose-950',
      brandName: 'Cromer & District Funeral Services',
      primaryBtn: 'bg-slate-800 hover:bg-slate-700 text-slate-200',
      activeTabStyle: 'border-rose-500 text-rose-400 bg-rose-950/20'
    },
    gowards: {
      bannerGradient: 'from-emerald-950 via-slate-950 to-emerald-950',
      brandName: 'Gowards Funeral Services',
      primaryBtn: 'bg-slate-800 hover:bg-slate-700 text-slate-200',
      activeTabStyle: 'border-emerald-500 text-emerald-400 bg-emerald-950/20'
    }
  }), []);

  const currentTheme = brandThemes[activeBrand];

  const getQrCodeUrl = (record, size = 200) => {
    if (!record) return '';
    let origin = window.location.origin || "https://cromer-gowards-mortuary.web.app";
    const deepLinkUrl = `${origin}${window.location.pathname}?case=${record.id}`;
    return `https://api.qrserver.com/v1/create-qr-code/?size=${size}x${size}&data=${encodeURIComponent(deepLinkUrl)}&bgcolor=f8fafc&color=0f172a`;
  };

  const handleFieldChange = async (id, fieldName, value) => {
    setDeceasedList(prev => prev.map(item => item.id === id ? { ...item, [fieldName]: value } : item));
    if (!isAuth) return;
    const docRef = doc(db, 'artifacts', appId, 'public', 'data', 'caseload', id);
    try {
      await updateDoc(docRef, { [fieldName]: value });
    } catch (error) {
      console.error("Firestore update failed:", error);
    }
  };

  const handleStatusChange = (id, newStatus) => {
    const timestamp = getTimestamp();
    const currentTimestamps = selectedRecord?.pickupStatusTimestamps || {};
    const updatedTimestamps = {
      ...currentTimestamps,
      [newStatus]: timestamp
    };
    handleFieldChange(id, 'pickupStatus', newStatus);
    handleFieldChange(id, 'pickupStatusTimestamps', updatedTimestamps);
  };

  const handleArchiveToggle = async (id) => {
    const item = deceasedList.find(d => d.id === id);
    if (!item) return;
    const updatedArchiveState = !item.isArchived;
    setDeceasedList(prev => prev.map(d => d.id === id ? { ...d, isArchived: updatedArchiveState } : d));
    
    if (isAuth) {
      const docRef = doc(db, 'artifacts', appId, 'public', 'data', 'caseload', id);
      try {
        await updateDoc(docRef, { isArchived: updatedArchiveState });
      } catch (error) {
        console.error("Firestore archive field toggling failed:", error);
      }
    }
    showNotification(
      updatedArchiveState ? "Record Archived" : "Record Restored",
      `The file for ${item.deceasedName || "Unnamed Admission"} was moved successfully.`,
      "info"
    );
  };

  const handleStaffToggle = (staffName, staffEmail) => {
    if (!selectedRecord) return;
    const currentStaff = selectedRecord.pickupStaff || [];
    let updatedStaff = [...currentStaff];
    
    if (updatedStaff.includes(staffName)) {
      updatedStaff = updatedStaff.filter(s => s !== staffName);
    } else {
      updatedStaff.push(staffName);
    }
    const selectedEmails = norfolkStaffList.filter(s => updatedStaff.includes(s.name)).map(s => s.email).join(', ');
    handleFieldChange(selectedRecord.id, 'pickupStaff', updatedStaff);
    handleFieldChange(selectedRecord.id, 'pickupStaffEmails', selectedEmails);
  };

  const handleEquipmentToggle = (equipName) => {
    if (!selectedRecord) return;
    const currentEquip = selectedRecord.pickupEquipment || [];
    let updatedEquip = [...currentEquip];
    if (updatedEquip.includes(equipName)) {
      updatedEquip = updatedEquip.filter(e => e !== equipName);
    } else {
      updatedEquip.push(equipName);
    }
    handleFieldChange(selectedRecord.id, 'pickupEquipment', updatedEquip);
  };

  const createAdmission = async (isCoronerCase) => {
    const nextId = String(Date.now());
    const newCase = {
      id: nextId,
      ref: `26/C/${String(deceasedList.length + 1).padStart(3, '0')}`,
      fridgeTray: "",
      keyDate: "",
      deceasedName: "", // Ghost placeholder targets empty string
      title: "Mr",
      dob: "", // Ghost placeholder targets empty string
      dod: "", // Ghost placeholder targets empty string
      arranger: "CRM",
      location: activeBrand === "gowards" ? "Fakenham" : "Cromer",
      greenCoroner: "No",
      encoffined: "No",
      plate: "No",
      bodySize: "",
      condition: "Good",
      infection: "None",
      coffin: "Chiltern Oak",
      clothes: "",
      clothesChecked: false,
      preparations: "No",
      preparationsDetails: "",
      jewellery: "No",
      jewelleryDetails: "",
      devices: "No",
      devicesDetails: "",
      embalming: "No",
      embalmingDetails: "",
      coffinAccessories: "",
      viewing: "R",
      ready: "No",
      isCoroner: isCoronerCase,
      coronerRef: "", // Ghost placeholder targets empty string
      coronerOfficer: "",
      pickupLocation: "",
      pickupDestination: activeBrand === "gowards" ? "Fakenham Mortuary" : "Cromer Mortuary",
      pickupDateTime: "",
      pickupStaff: [],
      pickupStaffEmails: "",
      pickupVehicle: "Vauxhall Vivaro CRM-1",
      pickupEquipment: ["First Call Stretcher"],
      pickupStatus: "Pending",
      pickupStatusTimestamps: {
        "Pending": getTimestamp()
      },
      pickupInstructions: "",
      isArchived: false
    };

    setDeceasedList(prev => [...prev, newCase]);
    setSelectedRowId(nextId);
    setActiveTab(isCoronerCase ? "pickup" : "care");

    if (isAuth) {
      const docRef = doc(db, 'artifacts', appId, 'public', 'data', 'caseload', nextId);
      try {
        await setDoc(docRef, newCase);
      } catch (error) {
        console.error("Firestore create failed:", error);
      }
    }
  };

  const confirmCaseDeletion = (id, name) => {
    setDialog({
      isOpen: true,
      title: "Confirm Case Removal",
      message: `Are you certain you want to remove the care profile for ${name || "this case"}? This action deletes the cloud copy permanently.`,
      type: "confirm",
      onConfirm: async () => {
        if (isAuth) {
          const docRef = doc(db, 'artifacts', appId, 'public', 'data', 'caseload', id);
          try {
            await deleteDoc(docRef);
          } catch (error) {
            console.error("Firestore delete failed:", error);
          }
        } else {
          setDeceasedList(prev => prev.filter(item => item.id !== id));
        }
        if (selectedRowId === id) setSelectedRowId(null);
        closeDialog();
        showNotification("Case Removed", "The deceased record was removed from active custody registers.", "info");
      }
    });
  };

  const showNotification = (title, message, type = "info") => {
    setDialog({ isOpen: true, title, message, type, onConfirm: null });
  };

  const closeDialog = () => {
    setDialog({ isOpen: false, title: "", message: "", type: "info", onConfirm: null });
  };

  const printDocHeader = (record, docTitle) => {
    const origin = window.location.origin || "https://cromer-gowards-mortuary.web.app";
    const deepLinkUrl = `${origin}${window.location.pathname}?case=${record?.id}`;
    const qrCodeUrl = `https://api.qrserver.com/v1/create-qr-code/?size=70x70&data=${encodeURIComponent(deepLinkUrl)}&bgcolor=ffffff&color=000000`;

    return `
      <div style="border-bottom: 3px double #000; padding-bottom: 12px; margin-bottom: 20px; display: flex; justify-content: space-between; align-items: center; font-family: 'Segoe UI', Arial, sans-serif;">
        <div>
          <h1 style="font-size: 18px; font-weight: 900; text-transform: uppercase; margin: 0; line-height: 1.2;">${currentTheme.brandName}</h1>
          <h2 style="font-size: 13px; font-weight: bold; text-transform: uppercase; margin: 4px 0 0 0; color: #444;">${docTitle}</h2>
        </div>
        <div style="display: flex; align-items: center; gap: 15px;">
          <div style="text-align: right;">
            <span style="font-size: 12px; font-weight: bold; font-family: monospace; background: #e2e8f0; padding: 3px 8px; border: 1px solid #000; border-radius: 4px;">ARR: ${record?.ref}</span>
            <div style="font-size: 9px; color: #555; margin-top: 5px;">Printed: ${getTimestamp().split(' ')[0]}</div>
          </div>
          <div style="border: 1px solid #000; padding: 2px; background: #fff; width: 60px; height: 60px; display: flex; align-items: center; justify-content: center;">
            <img src="${qrCodeUrl}" alt="QR Link" style="width: 100%; height: 100%; object-fit: contain;" />
          </div>
        </div>
      </div>
    `;
  };

  const printRecordCard = (record) => `
    <div style="border: 1px solid #000; padding: 12px; background: #f8fafc; border-radius: 6px; margin-bottom: 15px; display: grid; grid-template-columns: 1fr 1fr; gap: 10px; font-size: 12px; font-family: 'Segoe UI', Arial, sans-serif;">
      <div><strong>Deceased:</strong> ${record?.title} ${record?.deceasedName || "Unnamed Admission"}</div>
      <div><strong>Tray Assignment:</strong> ${record?.fridgeTray || 'PENDING'}</div>
      <div><strong>Date of Birth:</strong> ${record?.dob || 'PENDING'}</div>
      <div><strong>Date of Death:</strong> ${record?.dod || 'PENDING'}</div>
      <div><strong>Branch Location:</strong> ${record?.location}</div>
      <div><strong>Case Type:</strong> ${record?.isCoroner ? '⚖️ Coroner Mandate' : 'Standard Private'}</div>
    </div>
  `;

  const printCareDocument = (record) => {
    const printWindow = window.open('', '_blank');
    if (!printWindow) {
      showNotification("Pop-up Blocked", "Please allow pop-ups to print the Clinical Care sheet.", "info");
      return;
    }
    printWindow.document.write(`
      <html>
        <head>
          <title>Clinical Care Report - ${record?.deceasedName || "Unnamed Case"}</title>
          <style>
            body { font-family: 'Segoe UI', Arial, sans-serif; padding: 40px; color: #000; background: #fff; line-height: 1.5; }
            .section { border: 1px solid #000; border-radius: 6px; padding: 15px; margin-bottom: 15px; }
            .section-title { font-size: 12px; font-weight: bold; text-transform: uppercase; background: #e2e8f0; padding: 4px 8px; border-bottom: 1px solid #000; margin: -15px -15px 12px -15px; border-top-left-radius: 5px; border-top-right-radius: 5px; }
            .field-row { display: flex; justify-content: space-between; padding: 5px 0; border-bottom: 1px dashed #eee; font-size: 13px; }
            .hazard-alert { background: #fee2e2; border: 2px solid #ef4444; color: #991b1b; padding: 10px; border-radius: 6px; font-weight: bold; text-align: center; margin-bottom: 15px; }
          </style>
        </head>
        <body onload="window.print()">
          ${printDocHeader(record, "Clinical Mortuary & Registration Record")}
          ${printRecordCard(record)}
          
          ${record?.infection && record?.infection !== 'None' ? `
            <div class="hazard-alert">
              🚨 BIO-HAZARD PROTOCOLS ACTIVE: ${record.infection.toUpperCase()}
            </div>
          ` : ''}

          <div class="section">
            <div class="section-title">Anatomical & Care Status</div>
            <div class="field-row"><span>Body Condition Score:</span> <strong>${record?.condition}</strong></div>
            <div class="field-row"><span>Implants/Defibrillators:</span> <strong>${record?.devicesDetails || 'None Registered'}</strong></div>
            <div class="field-row"><span>Embalming Action:</span> <strong>${record?.embalmingDetails || 'None'}</strong></div>
            <div class="field-row"><span>Key Milestone Date:</span> <strong>${record?.keyDate || 'Pending'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">Sanitary Preparation & Grooming</div>
            <div style="font-size: 13px; white-space: pre-wrap;">${record?.preparationsDetails || 'Standard sanitary preparations only.'}</div>
          </div>

          <div class="section">
            <div class="section-title">Valuables & Jewellery Custody Register</div>
            <div style="font-size: 13px; white-space: pre-wrap;">${record?.jewelleryDetails || 'No personal effects logged.'}</div>
          </div>
        </body>
      </html>
    `);
    printWindow.document.close();
  };

  const printWorkshopDocument = (record) => {
    const printWindow = window.open('', '_blank');
    if (!printWindow) {
      showNotification("Pop-up Blocked", "Please allow pop-ups to print the Coffin Spec Sheet.", "info");
      return;
    }
    printWindow.document.write(`
      <html>
        <head>
          <title>Joinery Workshop Spec - ${record?.deceasedName || "Unnamed Case"}</title>
          <style>
            body { font-family: 'Segoe UI', Arial, sans-serif; padding: 40px; color: #000; background: #fff; line-height: 1.5; }
            .section { border: 1px solid #000; border-radius: 6px; padding: 15px; margin-bottom: 15px; }
            .section-title { font-size: 12px; font-weight: bold; text-transform: uppercase; background: #e2e8f0; padding: 4px 8px; border-bottom: 1px solid #000; margin: -15px -15px 12px -15px; border-top-left-radius: 5px; border-top-right-radius: 5px; }
            .field-row { display: flex; justify-content: space-between; padding: 5px 0; border-bottom: 1px dashed #eee; font-size: 13px; }
          </style>
        </head>
        <body onload="window.print()">
          ${printDocHeader(record, "Coffin Joinery & Workshop Specification")}
          ${printRecordCard(record)}

          <div class="section">
            <div class="section-title">1. Coffin Construction Dimensions</div>
            <div class="field-row"><span>Timber Specification:</span> <strong>${record?.coffin}</strong></div>
            <div class="field-row"><span>Mountings & Linings:</span> <strong>${record?.coffinAccessories || 'Standard Spec'}</strong></div>
            <div class="field-row"><span>Dimensions (Body Size):</span> <strong style="font-size: 16px; font-family: monospace;">${record?.bodySize || 'PENDING SPEC'}</strong></div>
            <div class="field-row"><span>Engraved Name Plate Fixed:</span> <strong>${record?.plate || 'No'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">2. Dressing Attire & Verification</div>
            <div class="field-row"><span>Selected Apparel:</span> <strong>${record?.clothes || 'None Specified'}</strong></div>
            <div class="field-row"><span>Apparel Received & Verified:</span> <strong>${record?.clothesChecked ? '✓ Yes (Verified)' : '✗ Pending Receipt'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">3. Viewing Milestones</div>
            <div class="field-row"><span>Family Viewing Request:</span> <strong>${record?.viewing === 'Yes' ? '✓ CONFIRMED' : record?.viewing === 'No' ? '✗ DECLINED' : 'R - REQUESTED'}</strong></div>
            <div class="field-row"><span>Ready for Placement:</span> <strong>${record?.ready || 'No'}</strong></div>
          </div>
        </body>
      </html>
    `);
    printWindow.document.close();
  };

  const printCoronerDocument = (record) => {
    if (!record?.isCoroner) return;
    const printWindow = window.open('', '_blank');
    if (!printWindow) {
      showNotification("Pop-up Blocked", "Please allow pop-ups to print the Coroner Dispatch sheet.", "info");
      return;
    }
    
    let timelineHtml = '';
    if (record?.pickupStatusTimestamps) {
      Object.entries(record.pickupStatusTimestamps).forEach(([status, time]) => {
        timelineHtml += `<div class="timeline-item"><strong>${status}:</strong> <span>${time}</span></div>`;
      });
    }

    printWindow.document.write(`
      <html>
        <head>
          <title>Coroner Dispatch Sheet - ${record?.deceasedName || "Unnamed Case"}</title>
          <style>
            body { font-family: 'Segoe UI', Arial, sans-serif; padding: 40px; color: #000; background: #fff; line-height: 1.5; }
            .section { border: 1px solid #000; border-radius: 6px; padding: 15px; margin-bottom: 15px; }
            .section-title { font-size: 12px; font-weight: bold; text-transform: uppercase; background: #e2e8f0; padding: 4px 8px; border-bottom: 1px solid #000; margin: -15px -15px 12px -15px; border-top-left-radius: 5px; border-top-right-radius: 5px; }
            .field-row { display: flex; justify-content: space-between; padding: 5px 0; border-bottom: 1px dashed #eee; font-size: 13px; }
            .timeline-box { background: #f8fafc; border: 1px solid #cbd5e1; border-radius: 4px; padding: 10px; margin-top: 10px; }
            .timeline-item { display: flex; justify-content: space-between; font-size: 12px; font-family: monospace; padding: 4px 0; border-bottom: 1px solid #e2e8f0; }
            .timeline-item:last-child { border: none; }
          </style>
        </head>
        <body onload="window.print()">
          ${printDocHeader(record, "Coroner's Removal Authority & Dispatch")}
          ${printRecordCard(record)}

          <div class="section">
            <div class="section-title">Coroner Authority Details</div>
            <div class="field-row"><span>CAD Reference:</span> <strong>${record?.coronerRef || 'N/A'}</strong></div>
            <div class="field-row"><span>Instructing Officer:</span> <strong>${record?.coronerOfficer || 'N/A'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">Removal Logistics & Fleet</div>
            <div class="field-row"><span>Pickup Location:</span> <strong>${record?.pickupLocation || 'PENDING'}</strong></div>
            <div class="field-row"><span>Destination:</span> <strong>${record?.pickupDestination || 'Cromer'}</strong></div>
            <div class="field-row"><span>Scheduled Time:</span> <strong>${record?.pickupDateTime || 'PENDING'}</strong></div>
            <div class="field-row"><span>Assigned Fleet Vehicle:</span> <strong>${record?.pickupVehicle || 'N/A'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">Road Crew & Equipment Checks</div>
            <div class="field-row"><span>Crew Dispatched:</span> <strong>${(record?.pickupStaff || []).join(', ') || 'PENDING'}</strong></div>
            <div class="field-row"><span>Mobilised Equipment:</span> <strong>${(record?.pickupEquipment || []).join(', ') || 'First Call Stretcher'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">Live Dispatch Audits</div>
            <div class="field-row"><span>Current Mission Stage:</span> <strong style="text-transform: uppercase; color: #b45309;">${record?.pickupStatus}</strong></div>
            <div class="timeline-box">
              <div style="font-size: 10px; font-weight: bold; margin-bottom: 5px; text-transform: uppercase; color: #475569;">Stage Logs:</div>
              ${timelineHtml || '<span style="font-size: 12px; color: #64748b;">No log updates recorded.</span>'}
            </div>
          </div>
        </body>
      </html>
    `);
    printWindow.document.close();
  };

  const printCombinedMasterDocument = (record) => {
    const printWindow = window.open('', '_blank');
    if (!printWindow) {
      showNotification("Pop-up Blocked", "Please allow pop-ups to print the Combined Master Record.", "info");
      return;
    }

    let timelineHtml = '';
    if (record?.pickupStatusTimestamps) {
      Object.entries(record.pickupStatusTimestamps).forEach(([status, time]) => {
        timelineHtml += `<div class="timeline-item"><strong>${status}:</strong> <span>${time}</span></div>`;
      });
    }

    printWindow.document.write(`
      <html>
        <head>
          <title>Master Case Record - ${record?.deceasedName || "Unnamed Case"}</title>
          <style>
            body { font-family: 'Segoe UI', Arial, sans-serif; padding: 40px; color: #000; background: #fff; line-height: 1.4; }
            .section { border: 1px solid #000; border-radius: 6px; padding: 12px; margin-bottom: 12px; page-break-inside: avoid; }
            .section-title { font-size: 11px; font-weight: bold; text-transform: uppercase; background: #334155; color: #fff; padding: 4px 8px; border-bottom: 1px solid #000; margin: -12px -12px 10px -12px; border-top-left-radius: 5px; border-top-right-radius: 5px; }
            .field-row { display: flex; justify-content: space-between; padding: 4px 0; border-bottom: 1px dashed #eee; font-size: 12px; }
            .timeline-box { background: #f8fafc; border: 1px solid #cbd5e1; border-radius: 4px; padding: 8px; margin-top: 8px; }
            .timeline-item { display: flex; justify-content: space-between; font-size: 11px; font-family: monospace; padding: 3px 0; border-bottom: 1px solid #e2e8f0; }
            .timeline-item:last-child { border: none; }
            .hazard-alert { background: #fee2e2; border: 2px solid #ef4444; color: #991b1b; padding: 8px; border-radius: 6px; font-weight: bold; text-align: center; margin-bottom: 12px; font-size: 12px; }
            .page-break { page-break-before: always; }
          </style>
        </head>
        <body onload="window.print()">
          ${printDocHeader(record, "MASTER CUSTODY REGISTER & LOGS (COMBINED FILE)")}
          ${printRecordCard(record)}

          ${record?.infection && record?.infection !== 'None' ? `
            <div class="hazard-alert">
              🚨 BIO-HAZARD PROTOCOLS MANDATORY: ${record.infection.toUpperCase()}
            </div>
          ` : ''}

          <div class="section">
            <div class="section-title">Clinical & Care Registry Details</div>
            <div class="field-row"><span>Body Condition:</span> <strong>${record?.condition}</strong></div>
            <div class="field-row"><span>Defibrillators/Pacemaker:</span> <strong>${record?.devicesDetails || 'None'}</strong></div>
            <div class="field-row"><span>Green Form Filed:</span> <strong>${record?.greenCoroner || 'No'}</strong></div>
            <div class="field-row"><span>Embalming Logs:</span> <strong>${record?.embalmingDetails || 'None'}</strong></div>
            <div class="field-row"><span>Key Milestone Date:</span> <strong>${record?.keyDate || 'Pending'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">Sanitary Preparations</div>
            <div style="font-size: 12px; white-space: pre-wrap;">${record?.preparationsDetails || 'Standard sanitary preparations registered.'}</div>
          </div>

          <div class="section">
            <div class="section-title">Jewellery, Valuables & Effects Custody Register</div>
            <div style="font-size: 12px; white-space: pre-wrap;">${record?.jewelleryDetails || 'No jewellery or personal effects currently logged.'}</div>
          </div>

          <div class="page-break"></div>

          ${printDocHeader(record, "MASTER CUSTODY REGISTER & LOGS (COMBINED FILE) - PAGE 2")}

          <div class="section">
            <div class="section-title">Coffin Construction Specs</div>
            <div class="field-row"><span>Timber Specification:</span> <strong>${record?.coffin}</strong></div>
            <div class="field-row"><span>Linings & Accessories:</span> <strong>${record?.coffinAccessories || 'Standard Spec'}</strong></div>
            <div class="field-row"><span>Joinery Dimensions:</span> <strong>${record?.bodySize || 'PENDING SPEC'}</strong></div>
            <div class="field-row"><span>Engraved Plate Affixed:</span> <strong>${record?.plate || 'No'}</strong></div>
            <div class="field-row"><span>Preparation Complete:</span> <strong>${record?.ready || 'No'}</strong></div>
          </div>

          <div class="section">
            <div class="section-title">Dressing & Viewing Details</div>
            <div class="field-row"><span>Dressing Apparel:</span> <strong>${record?.clothes || 'None'}</strong></div>
            <div class="field-row"><span>Apparel Checked/Received:</span> <strong>${record?.clothesChecked ? 'Yes' : 'No'}</strong></div>
            <div class="field-row"><span>Family Viewing Status:</span> <strong>${record?.viewing || 'Requested'}</strong></div>
          </div>

          ${record?.isCoroner ? `
            <div class="section">
              <div class="section-title">Coroner Authority Details & Logistics</div>
              <div class="field-row"><span>CAD Ref:</span> <strong>${record.coronerRef || 'N/A'}</strong></div>
              <div class="field-row"><span>Coroner Officer:</span> <strong>${record.coronerOfficer || 'N/A'}</strong></div>
              <div class="field-row"><span>Pick-up Location:</span> <strong>${record.pickupLocation || 'N/A'}</strong></div>
              <div class="field-row"><span>Scheduled Date:</span> <strong>${record.pickupDateTime || 'N/A'}</strong></div>
              <div class="field-row"><span>Assigned Fleet Vehicle:</span> <strong>${record.pickupVehicle || 'N/A'}</strong></div>
              <div class="field-row"><span>Mobilised Crew:</span> <strong>${(record.pickupStaff || []).join(', ') || 'N/A'}</strong></div>
              <div class="field-row"><span>Mobilised Gear:</span> <strong>${(record.pickupEquipment || []).join(', ') || 'N/A'}</strong></div>
              <div class="field-row"><span>Stage Status:</span> <strong>${record.pickupStatus || 'N/A'}</strong></div>
              
              <div class="timeline-box">
                <div style="font-size: 9px; font-weight: bold; margin-bottom: 4px; text-transform: uppercase; color: #475569;">Stage Timeline Logs:</div>
                ${timelineHtml || '<span style="font-size: 11px; color: #64748b;">No log updates recorded.</span>'}
              </div>
            </div>
          ` : ''}
        </body>
      </html>
    `);
    printWindow.document.close();
  };

  const printStickerAndCheckBlocks = (record) => {
    let origin = window.location.origin || "https://cromer-gowards-mortuary.web.app";
    const deepLinkUrl = origin + window.location.pathname + '?case=' + record?.id;
    const qrImgUrl = "https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=" + encodeURIComponent(deepLinkUrl) + "&bgcolor=ffffff&color=000000";

    const printWindow = window.open('', '_blank');
    if (!printWindow) {
      showNotification("Pop-up Blocked", "Your browser is blocking the print window. Please allow pop-ups for this site to print the sticker.", "info");
      return;
    }
    printWindow.document.write(`
    <html>
      <head>
        <title>COFFIN STICKER - ${record?.ref}</title>
        <style>
          @page { size: 4in 3in; margin: 0mm; }
          body { font-family: 'Arial', sans-serif; margin: 0; padding: 12px; background: #fff; color: #000; width: 3.8in; height: 2.8in; box-sizing: border-box; display: flex; flex-direction: column; justify-content: center; }
          .sticker-container { border: 3px solid #000; height: 100%; padding: 10px; box-sizing: border-box; display: flex; flex-direction: row; align-items: center; justify-content: space-between; }
          .details { width: 55%; display: flex; flex-direction: column; justify-content: center; gap: 12px; }
          .name { font-size: 20px; font-weight: 900; text-transform: uppercase; line-height: 1.2; word-wrap: break-word; }
          .dob-container { font-size: 14px; font-weight: bold; border-top: 2px solid #000; padding-top: 6px; }
          .dob-label { font-size: 10px; text-transform: uppercase; color: #555; display: block; margin-bottom: 2px; }
          .dob-value { font-family: monospace; font-size: 15px; }
          .qr-side { width: 40%; text-align: center; display: flex; flex-direction: column; align-items: center; justify-content: center; }
          .qr-side img { width: 100px; height: 100px; border: 1px solid #000; display: block; }
          .qr-caption { font-size: 8px; font-weight: bold; margin-top: 4px; letter-spacing: 0.5px; text-transform: uppercase; }
        </style>
      </head>
      <body onload="window.print()">
        <div class="sticker-container">
          <div class="details">
            <div class="name">${record?.title} ${record?.deceasedName || "Unnamed Case"}</div>
            <div class="dob-container">
              <span class="dob-label">Date of Birth (D.O.B.)</span>
              <span class="dob-value">${record?.dob || 'PENDING'}</span>
            </div>
          </div>
          <div class="qr-side">
            <img src="${qrImgUrl}" alt="Sticker QR Code" />
            <span class="qr-caption">Scan for Care File</span>
          </div>
        </div>
      </body>
    </html>
    `);
    printWindow.document.close();
  };

  const dispatchEmailData = useMemo(() => {
    if (!selectedRecord) return null;
    const subject = `🚨 CORONER DISPATCH: Removal Call - ${(selectedRecord?.title || '')} ${(selectedRecord?.deceasedName || '')} (${(selectedRecord?.ref || '')})`;
    const body = `CROMER & DISTRICT / GOWARDS FUNERAL SERVICES\n` +
      `CORONER'S PICK-UP DISPATCH INSTRUCTION\n` +
      `----------------------------------------\n\n` +
      `ARR Ref: ${(selectedRecord?.ref || '')}\n` +
      `Deceased Name: ${(selectedRecord?.title || '')} ${(selectedRecord?.deceasedName || 'Unnamed')}\n` +
      `CAD: ${(selectedRecord?.coronerRef || 'N/A')}\n` +
      `Coroner Officer: ${(selectedRecord?.coronerOfficer || 'N/A')}\n\n` +
      `Pick-up Location: ${(selectedRecord?.pickupLocation || 'PENDING')}\n` +
      `Target Destination: ${(selectedRecord?.pickupDestination || 'PENDING')}\n` +
      `Scheduled Date/Time: ${(selectedRecord?.pickupDateTime || 'PENDING')}\n\n` +
      `Vehicle Assigned: ${(selectedRecord?.pickupVehicle || 'Vauxhall Vivaro CRM-1')}\n` +
      `Staff Dispatched: ${(selectedRecord?.pickupStaff || []).join(', ') || 'PENDING'}\n` +
      `Equipment Checklist: ${(selectedRecord?.pickupEquipment || []).join(', ') || 'First Call Stretcher'}\n\n` +
      `SPECIAL INSTRUCTIONS:\n` +
      `- ${(selectedRecord?.pickupInstructions || 'Standard pick-up procedures.')}\n` +
      `----------------------------------------\n`;

    const mailtoLink = `mailto:${encodeURIComponent(selectedRecord?.pickupStaffEmails || '')}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
    return { subject, body, mailtoLink };
  }, [selectedRecord]);

  const filteredList = useMemo(() => {
    return deceasedList.filter(item => {
      const matchSearch = item.deceasedName.toLowerCase().includes(searchQuery.toLowerCase()) || 
                          item.ref.toLowerCase().includes(searchQuery.toLowerCase());
      const matchLoc = locationFilter === "All" || item.location === locationFilter;
      const matchStatus = statusFilter === "Active" ? !item.isArchived : item.isArchived;
      return matchSearch && matchLoc && matchStatus;
    });
  }, [deceasedList, searchQuery, locationFilter, statusFilter]);

  return (
    <div className="min-h-screen bg-slate-900 text-slate-100 flex flex-col font-sans overflow-hidden">
      
      {/* Brand Subheader */}
      <div className="bg-slate-950 text-xs py-2 px-6 flex flex-wrap items-center justify-between border-b border-slate-800/60 z-30 font-medium">
        <div className="flex items-center space-x-2 text-slate-400">
          <Building2 size={13} className="text-amber-500" />
          <span className="font-bold tracking-wide uppercase text-[10px]">Corporate Theme:</span>
        </div>
        <div className="flex items-center space-x-2">
          <button onClick={() => setActiveBrand("joint")} className={`px-3 py-1 rounded transition text-[11px] font-bold ${activeBrand === "joint" ? "bg-amber-500 text-slate-950" : "bg-slate-900 text-slate-300 hover:bg-slate-800"}`}>⚜️ Joint Group</button>
          <button onClick={() => setActiveBrand("cromer")} className={`px-3 py-1 rounded transition text-[11px] font-bold ${activeBrand === "cromer" ? "bg-rose-950 text-white" : "bg-slate-900 text-slate-300 hover:bg-slate-800"}`}>🏛️ Cromer</button>
          <button onClick={() => setActiveBrand("gowards")} className={`px-3 py-1 rounded transition text-[11px] font-bold ${activeBrand === "gowards" ? "bg-emerald-850 text-white" : "bg-slate-900 text-slate-300 hover:bg-slate-800"}`}>🌲 Gowards</button>
        </div>
      </div>

      {/* Main Header */}
      <header className={`bg-gradient-to-r ${currentTheme.bannerGradient} border-b border-slate-800 px-6 py-4 flex justify-between items-center z-10`}>
        <div className="flex items-center space-x-3.5">
          <div className="bg-slate-950 p-2 rounded-lg border border-slate-800">
            <span className="text-2xl">{activeBrand === "joint" ? "⚜️" : activeBrand === "cromer" ? "🏛️" : "🌲"}</span>
          </div>
          <div>
            <h1 className="text-xl font-black text-white">{currentTheme.brandName}</h1>
            <div className="flex items-center space-x-2 mt-1">
              <span className="bg-slate-950 text-amber-400 text-[10px] px-2 py-0.5 rounded-full font-bold border border-slate-800 uppercase">Mortuary Management</span>
              {isAuth ? <span className="text-[10px] text-emerald-400 font-bold flex items-center gap-1"><Cloud size={10}/> Cloud Sync</span> : <span className="text-[10px] text-rose-400 font-bold flex items-center gap-1"><CloudOff size={10}/> Offline Mode</span>}
            </div>
          </div>
        </div>
        <div className="flex gap-3">
          <button onClick={() => createAdmission(true)} className="px-4 py-2 rounded-lg flex items-center gap-2 text-xs font-black bg-rose-600 hover:bg-rose-500 text-white border border-rose-500/50 shadow-md transition transform active:scale-95">
            <AlertTriangle size={16} /> Record a Coroner's
          </button>
          <button onClick={() => createAdmission(false)} className={`px-4 py-2 rounded-lg flex items-center gap-2 text-xs font-black ${currentTheme.primaryBtn} border border-slate-700 shadow-md transition transform active:scale-95`}>
            <Plus size={16} /> Quick Add Admission
          </button>
        </div>
      </header>

      {/* Main Content Area */}
      {!selectedRowId ? (
        // DASHBOARD VIEW
        <div className="flex-1 flex flex-col p-6 overflow-hidden">
          <div className="flex items-center justify-between mb-6">
            <div className="flex items-center space-x-3">
              <h2 className="text-lg font-black text-white">Active Case Dashboard</h2>
              <select value={locationFilter} onChange={(e) => setLocationFilter(e.target.value)} className="bg-slate-950 border border-slate-800 text-xs text-slate-200 font-bold p-1.5 rounded-lg focus:outline-none">
                <option value="All">All Branches</option>
                {locations.map(loc => <option key={loc} value={loc}>{loc}</option>)}
              </select>
              <select value={statusFilter} onChange={(e) => setStatusFilter(e.target.value)} className="bg-slate-950 border border-slate-800 text-xs text-slate-200 font-bold p-1.5 rounded-lg focus:outline-none">
                <option value="Active">📁 Active Custody ({deceasedList.filter(d => !d.isArchived).length})</option>
                <option value="Archived">🗃️ Archived Files ({deceasedList.filter(d => d.isArchived).length})</option>
              </select>
            </div>
            <div className="relative w-64">
              <Search className="absolute left-3 top-2 text-slate-500" size={16} />
              <input type="text" placeholder="Search case roster..." value={searchQuery} onChange={(e) => setSearchQuery(e.target.value)} className="bg-slate-950 border border-slate-800 rounded-lg pl-9 pr-4 py-2 text-xs text-slate-200 w-full focus:outline-none focus:border-amber-500" />
            </div>
          </div>

          <div className="flex-1 overflow-y-auto pr-2">
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
              {filteredList.map((item) => (
                <div 
                  key={item.id}
                  onClick={() => { setSelectedRowId(item.id); setActiveTab(item.isCoroner ? "pickup" : "care"); }}
                  className="bg-slate-950 border border-slate-800 rounded-xl p-4 cursor-pointer hover:border-amber-500/50 hover:bg-slate-900 transition flex flex-col relative animate-fade-in"
                >
                  <div className="flex justify-between items-start mb-3">
                    <div>
                      <span className="text-[10px] font-mono font-bold text-amber-400 bg-amber-950/30 px-2 py-0.5 rounded border border-amber-900/50">{item.ref}</span>
                      {item.isCoroner && <span className="ml-2 text-[9px] font-black text-rose-400 bg-rose-950/50 px-2 py-0.5 rounded border border-rose-900 uppercase">Coroner</span>}
                    </div>
                    
                    {/* Embedded dashboard tile actions */}
                    <div className="flex items-center space-x-1.5">
                      <div className="flex items-center space-x-1 bg-slate-900 px-1 py-0.5 rounded border border-slate-800">
                        <button 
                          title={item.isArchived ? "Restore File" : "Archive File"}
                          onClick={(e) => { e.stopPropagation(); handleArchiveToggle(item.id); }} 
                          className="p-1 rounded text-slate-400 hover:text-amber-400 hover:bg-slate-850 transition"
                        >
                          <FolderOpen size={13} />
                        </button>
                        <button 
                          title="Delete File"
                          onClick={(e) => { e.stopPropagation(); confirmCaseDeletion(item.id, item.deceasedName); }} 
                          className="p-1 rounded text-slate-400 hover:text-red-500 hover:bg-slate-850 transition"
                        >
                          <Trash2 size={13} />
                        </button>
                      </div>
                      <div className="bg-slate-900 p-1 rounded-full border border-slate-800">
                        <Heart size={14} className={item.condition === 'Poor' ? 'text-rose-500' : item.condition === 'Medium' ? 'text-amber-500' : 'text-emerald-500'} />
                      </div>
                    </div>
                  </div>
                  
                  <h3 className="text-base font-black text-white mb-1">{item.title} {item.deceasedName || "Unnamed Admission"}</h3>
                  <p className="text-xs text-slate-400 mb-4">{item.location} • Tray {item.fridgeTray || 'Pending'}</p>
                  
                  {item.isCoroner && (
                    <div className="mt-auto pt-3 border-t border-slate-800/60">
                      <div className="flex justify-between text-[10px] font-bold uppercase mb-1">
                        <span className="text-slate-500">Dispatch Stage:</span>
                        <span className="text-amber-400">{item.pickupStatus}</span>
                      </div>
                      <div className="w-full bg-slate-900 rounded-full h-1.5 border border-slate-800 overflow-hidden mb-1">
                        <div className="bg-amber-500 h-full" style={{ width: item.pickupStatus === 'Pending' ? '25%' : item.pickupStatus === 'Dispatched' ? '50%' : item.pickupStatus === 'On Scene' ? '75%' : '100%' }}></div>
                      </div>
                      {item.pickupStatusTimestamps?.[item.pickupStatus] && (
                        <div className="text-[9px] text-slate-400 text-right font-mono font-bold">
                          Logged: {item.pickupStatusTimestamps[item.pickupStatus]}
                        </div>
                      )}
                    </div>
                  )}
                  {!item.isCoroner && (
                    <div className="mt-auto pt-3 border-t border-slate-800/60 flex items-center justify-between text-[10px] font-bold text-slate-500">
                      <span>Coffin: <span className="text-slate-300">{item.coffin}</span></span>
                      {item.infection !== "None" && <span className="text-red-400">⚠️ {item.infection}</span>}
                    </div>
                  )}
                </div>
              ))}
            </div>
          </div>
        </div>
      ) : selectedRowId && !selectedRecord ? (
        <div className="flex-1 bg-slate-900 text-slate-100 flex flex-col justify-center items-center py-20">
          <div className="animate-spin rounded-full h-12 w-12 border-b-2 border-amber-500"></div>
          <p className="mt-4 text-xs font-bold text-slate-400">Loading Case File...</p>
        </div>
      ) : (
        // DETAILS VIEW
        <div className="flex-1 flex flex-col overflow-hidden bg-slate-900">
          <div className="bg-slate-950 border-b border-slate-800 flex items-center px-6 py-0">
            <button onClick={() => setSelectedRowId(null)} className="px-4 py-3 text-xs font-bold text-slate-400 hover:text-white flex items-center gap-2 border-r border-slate-800 mr-2">
              <ArrowLeft size={14} /> Dashboard
            </button>
            <button onClick={() => setActiveTab("care")} className={`px-5 py-3 text-xs font-bold tracking-wider uppercase border-b-2 flex items-center gap-2 ${activeTab === "care" ? currentTheme.activeTabStyle : 'border-transparent text-slate-400 hover:text-white'}`}>
              <Users size={14} /> 1. Deceased Care
            </button>
            <button onClick={() => setActiveTab("workshop")} className={`px-5 py-3 text-xs font-bold tracking-wider uppercase border-b-2 flex items-center gap-2 ${activeTab === "workshop" ? currentTheme.activeTabStyle : 'border-transparent text-slate-400 hover:text-white'}`}>
              <Hammer size={14} /> 2. Coffin Workshop
            </button>
            {selectedRecord?.isCoroner && (
              <button onClick={() => setActiveTab("pickup")} className={`px-5 py-3 text-xs font-bold tracking-wider uppercase border-b-2 flex items-center gap-2 ${activeTab === "pickup" ? currentTheme.activeTabStyle : 'border-transparent text-slate-400 hover:text-white'}`}>
                <Mail size={14} /> 3. Coroner's Dispatch
              </button>
            )}
          </div>

          <div className="flex-1 overflow-y-auto p-6">
            <div className="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-6">
              
              {/* LEFT COLUMN: EDITING CARDS */}
              <div className="lg:col-span-2 space-y-6">
                
                {/* CARE TAB FORM MODULES */}
                {activeTab === "care" && (
                  <>
                    <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                      <div className="flex items-center space-x-2 border-b border-slate-800 pb-3 mb-4"><Layers className="text-amber-500" size={16} /><h3 className="text-sm font-bold uppercase tracking-widest text-slate-300">Core Admission Details</h3></div>
                      <div className="grid grid-cols-6 gap-4 mb-4">
                        <div className="col-span-2">
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Title</label>
                          <select value={selectedRecord?.title || 'Mr'} onChange={(e) => handleFieldChange(selectedRecord.id, 'title', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold">
                            {titles.map(t => <option key={t} value={t}>{t}</option>)}
                          </select>
                        </div>
                        <div className="col-span-4">
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Deceased Name</label>
                          <input type="text" value={selectedRecord?.deceasedName || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'deceasedName', e.target.value)} placeholder="e.g. Dennis Harrison" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-white w-full focus:outline-none font-bold" />
                        </div>
                      </div>
                      <div className="grid grid-cols-2 lg:grid-cols-4 gap-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Branch</label>
                          <select value={selectedRecord?.location || 'Cromer'} onChange={(e) => handleFieldChange(selectedRecord.id, 'location', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none">
                            {locations.map(loc => <option key={loc} value={loc}>{loc}</option>)}
                          </select>
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Tray No.</label>
                          <input type="text" value={selectedRecord?.fridgeTray || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'fridgeTray', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-amber-400 font-bold w-full focus:outline-none text-center" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">D.O.B.</label>
                          <input type="text" value={selectedRecord?.dob || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'dob', e.target.value)} placeholder="DD/MM/YYYY" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-amber-400 font-bold w-full focus:outline-none" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">D.O.D.</label>
                          <input type="text" value={selectedRecord?.dod || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'dod', e.target.value)} placeholder="DD/MM/YYYY" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none" />
                        </div>
                      </div>
                    </div>

                    <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                      <div className="flex items-center space-x-2 border-b border-slate-800 pb-3 mb-4"><AlertTriangle className="text-red-500" size={16} /><h3 className="text-sm font-bold uppercase tracking-widest text-slate-300">Clinical Protocols & Hazards</h3></div>
                      <div className="grid grid-cols-2 gap-4 mb-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-red-400 block mb-1">Bio-Hazard Infection</label>
                          <select value={selectedRecord?.infection || 'None'} onChange={(e) => handleFieldChange(selectedRecord.id, 'infection', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-red-400 font-bold w-full focus:outline-none">
                            {infectionRisks.map(r => <option key={r} value={r}>{r}</option>)}
                          </select>
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Condition</label>
                          <select value={selectedRecord?.condition || 'Good'} onChange={(e) => handleFieldChange(selectedRecord.id, 'condition', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold">
                            {conditions.map(c => <option key={c} value={c}>{c}</option>)}
                          </select>
                        </div>
                      </div>
                      <div className="grid grid-cols-2 gap-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Implants/Devices</label>
                          <input type="text" value={selectedRecord?.devicesDetails || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'devicesDetails', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 w-full focus:outline-none font-bold text-amber-400" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Embalming Details</label>
                          <input type="text" value={selectedRecord?.embalmingDetails || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'embalmingDetails', e.target.value)} placeholder="e.g. Completed on DD/MM/YYYY" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none" />
                        </div>
                      </div>
                    </div>

                    <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                      <div className="flex items-center space-x-2 border-b border-slate-800 pb-3 mb-4"><Heart className="text-amber-500" size={16} /><h3 className="text-sm font-bold uppercase tracking-widest text-slate-300">Sanitary preparations</h3></div>
                      <div className="grid grid-cols-2 gap-4 mb-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Grooming & Sanitary</label>
                          <textarea value={selectedRecord?.preparationsDetails || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'preparationsDetails', e.target.value)} rows={3} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none resize-none" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Jewellery Custody</label>
                          <textarea value={selectedRecord?.jewelleryDetails || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'jewelleryDetails', e.target.value)} rows={3} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none resize-none" />
                        </div>
                      </div>
                      <div>
                        <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Key Milestone Date</label>
                        <input type="text" value={selectedRecord?.keyDate || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'keyDate', e.target.value)} placeholder="DD/MM/YYYY" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-amber-500 font-bold w-full max-w-xs focus:outline-none" />
                      </div>
                    </div>
                  </>
                )}

                {/* WORKSHOP TAB FORM MODULES */}
                {activeTab === "workshop" && (
                  <>
                    <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                      <div className="flex items-center space-x-2 border-b border-slate-800 pb-3 mb-4"><Hammer className="text-amber-500" size={16} /><h3 className="text-sm font-bold uppercase tracking-widest text-slate-300">Construction Specifications</h3></div>
                      <div className="grid grid-cols-3 gap-4 mb-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-amber-400 block mb-1">Selected Wood</label>
                          <select value={selectedRecord?.coffin || 'Chiltern Oak'} onChange={(e) => handleFieldChange(selectedRecord.id, 'coffin', e.target.value)} className="bg-slate-900 border border-amber-900/30 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold">
                            {coffinsList.map(c => <option key={c} value={c}>{c}</option>)}
                          </select>
                        </div>
                        <div className="col-span-2">
                          <label className="text-[10px] font-bold uppercase text-amber-400 block mb-1">Linings, Plates & Handles</label>
                          <input type="text" value={selectedRecord?.coffinAccessories || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'coffinAccessories', e.target.value)} className="bg-slate-900 border border-amber-900/30 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold text-amber-300" />
                        </div>
                      </div>
                      <div className="grid grid-cols-2 gap-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Body Size Dimensions</label>
                          <input type="text" value={selectedRecord?.bodySize || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'bodySize', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-white w-full focus:outline-none font-mono text-center font-bold" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Engraved Name Plate</label>
                          <select value={selectedRecord?.plate || 'No'} onChange={(e) => handleFieldChange(selectedRecord.id, 'plate', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-semibold text-center">
                            {triStateOptions.map(o => <option key={o} value={o}>{o}</option>)}
                          </select>
                        </div>
                      </div>
                    </div>

                    <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                      <div className="flex items-center space-x-2 border-b border-slate-800 pb-3 mb-4"><Users className="text-amber-500" size={16} /><h3 className="text-sm font-bold uppercase tracking-widest text-slate-300">Dressing & Viewings</h3></div>
                      <div className="grid grid-cols-2 gap-4 mb-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Dressing Attire</label>
                          <input type="text" value={selectedRecord?.clothes || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'clothes', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Family Viewing</label>
                          <select value={selectedRecord?.viewing || 'R'} onChange={(e) => handleFieldChange(selectedRecord.id, 'viewing', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold">
                            <option value="Yes">✓ Viewing Confirmed</option><option value="No">✗ Viewing Declined</option><option value="R">R Viewing Requested</option>
                          </select>
                        </div>
                      </div>
                    </div>
                  </>
                )}

                {/* CORONER TAB FORM MODULES */}
                {activeTab === "pickup" && selectedRecord?.isCoroner && (
                  <>
                    <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                      <div className="flex items-center space-x-2 border-b border-slate-800 pb-3 mb-4"><Building2 className="text-amber-500" size={16} /><h3 className="text-sm font-bold uppercase tracking-widest text-slate-300">Coroner Authority Details</h3></div>
                      
                      <div className="grid grid-cols-6 gap-4 mb-4">
                        <div className="col-span-2">
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Title</label>
                          <select value={selectedRecord?.title || 'Mr'} onChange={(e) => handleFieldChange(selectedRecord.id, 'title', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold">
                            {titles.map(t => <option key={t} value={t}>{t}</option>)}
                          </select>
                        </div>
                        <div className="col-span-4">
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Deceased Name</label>
                          <input type="text" value={selectedRecord?.deceasedName || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'deceasedName', e.target.value)} placeholder="e.g. Dennis Harrison" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-white w-full focus:outline-none font-bold" />
                        </div>
                      </div>
                      
                      <div className="grid grid-cols-2 gap-4 mb-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">D.O.B.</label>
                          <input type="text" value={selectedRecord?.dob || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'dob', e.target.value)} placeholder="DD/MM/YYYY" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-amber-400 font-bold w-full focus:outline-none" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">D.O.D.</label>
                          <input type="text" value={selectedRecord?.dod || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'dod', e.target.value)} placeholder="DD/MM/YYYY" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none" />
                        </div>
                      </div>

                      <div className="grid grid-cols-2 gap-4">
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">CAD</label>
                          <input type="text" value={selectedRecord?.coronerRef || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'coronerRef', e.target.value)} placeholder="e.g. CAD-10294-2026" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-white w-full focus:outline-none font-mono font-bold" />
                        </div>
                        <div>
                          <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Officer / Contact</label>
                          <input type="text" value={selectedRecord?.coronerOfficer || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'coronerOfficer', e.target.value)} placeholder="e.g. Officer J. Miller" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none" />
                        </div>
                      </div>
                    </div>

                    <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                      <div className="flex items-center space-x-2 border-b border-slate-800 pb-3 mb-4"><Truck className="text-amber-500" size={16} /><h3 className="text-sm font-bold uppercase tracking-widest text-slate-300">Logistics & Dispatch</h3></div>
                      
                      <div className="grid grid-cols-2 gap-5 mb-5">
                        <div>
                          <label className="text-[10px] font-black uppercase text-slate-400 block mb-2">Live Dispatch Stage:</label>
                          <div className="grid grid-cols-2 gap-2 mb-3">
                            {["Pending", "Dispatched", "On Scene", "Collected"].map((st) => {
                              const isCurrent = selectedRecord?.pickupStatus === st;
                              return (
                                <button key={st} type="button" onClick={() => handleStatusChange(selectedRecord.id, st)} className={`py-1.5 px-2 rounded text-xs font-black transition text-center uppercase tracking-wider ${isCurrent ? 'bg-amber-500 text-slate-950 shadow' : 'bg-slate-900 text-slate-400 hover:bg-slate-800'}`}>{st}</button>
                              );
                            })}
                          </div>
                          
                          {/* Live Dispatch Milestone Timestamps */}
                          <div className="bg-slate-900 p-2.5 rounded border border-slate-800 text-[11px] font-sans">
                            <span className="text-[9px] font-bold uppercase tracking-widest text-slate-400 block mb-1.5">Dispatch Milestone Log</span>
                            <div className="space-y-1">
                              {["Pending", "Dispatched", "On Scene", "Collected"].map((st) => {
                                const ts = selectedRecord?.pickupStatusTimestamps?.[st];
                                return (
                                  <div key={st} className="flex justify-between items-center py-0.5 border-b border-slate-800/40 last:border-0">
                                    <span className="text-slate-400 font-semibold">{st}:</span>
                                    <span className="font-mono text-amber-400">{ts || <span className="text-slate-600 font-sans italic">Not yet logged</span>}</span>
                                  </div>
                                );
                              })}
                            </div>
                          </div>
                        </div>
                        <div className="space-y-4">
                          <div>
                            <label className="text-[10px] font-black uppercase text-slate-400 block mb-2">Vehicle Assigned</label>
                            <select value={selectedRecord?.pickupVehicle || 'Vauxhall Vivaro CRM-1'} onChange={(e) => handleFieldChange(selectedRecord.id, 'pickupVehicle', e.target.value)} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-semibold">
                              {vehicleOptions.map(veh => <option key={veh} value={veh}>{veh}</option>)}
                            </select>
                          </div>
                          <div>
                            <label className="text-[10px] font-black uppercase text-slate-400 block mb-2">Scheduled Date & Time</label>
                            <input type="text" value={selectedRecord?.pickupDateTime || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'pickupDateTime', e.target.value)} placeholder="DD/MM/YYYY HH:MM" className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none font-bold text-amber-500" />
                          </div>
                        </div>
                      </div>
                      
                      <div className="mb-5">
                        <label className="text-[10px] font-black uppercase text-slate-400 block mb-2">Assigned Staff:</label>
                        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-2">
                          {norfolkStaffList.map((staff) => {
                            const isChecked = (selectedRecord?.pickupStaff || []).includes(staff.name);
                            return (
                              <div key={staff.id} onClick={() => handleStaffToggle(staff.name, staff.email)} className={`flex items-center space-x-2.5 p-2 rounded-lg border cursor-pointer select-none transition ${isChecked ? 'bg-amber-950/20 border-amber-500/50 text-white' : 'bg-slate-900/50 border-slate-800 text-slate-400 hover:bg-slate-800'}`}>
                                {isChecked ? <CheckSquare size={16} className="text-amber-400" /> : <Square size={16} className="text-slate-600" />}
                                <div className="text-xs font-bold">{staff.name}</div>
                              </div>
                            );
                          })}
                        </div>
                      </div>
                      
                      <div>
                        <label className="text-[10px] font-bold uppercase text-slate-400 block mb-1">Pick-up Address & Notes</label>
                        <textarea value={selectedRecord?.pickupLocation || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'pickupLocation', e.target.value)} rows={2} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none mb-2" placeholder="e.g. Norfolk & Norwich University Hospital (NNUH) - Pathology Entrance B" />
                        <textarea value={selectedRecord?.pickupInstructions || ''} onChange={(e) => handleFieldChange(selectedRecord.id, 'pickupInstructions', e.target.value)} rows={2} className="bg-slate-900 border border-slate-700 rounded text-xs p-2.5 text-slate-200 w-full focus:outline-none" placeholder="e.g. Bring identity collar tag and scoop stretcher." />
                      </div>
                    </div>

                    {/* Dispatch Emailer positioned above save button inside Tab 3 */}
                    {dispatchEmailData && (
                      <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg">
                        <div className="flex items-center space-x-1.5 text-slate-400 mb-3 border-b border-slate-800 pb-3">
                          <Mail size={14} className="text-amber-500" />
                          <span className="text-[10px] font-black tracking-widest uppercase">Dispatch Emailer</span>
                        </div>
                        <div className="space-y-2.5 bg-slate-900 p-3 rounded-lg border border-slate-800 text-xs font-mono">
                          <div className="text-slate-400 font-bold">To: <span className="text-slate-200 block font-normal text-[11px] truncate bg-slate-950 p-1.5 border border-slate-800 mt-1">{selectedRecord?.pickupStaffEmails || 'None'}</span></div>
                        </div>
                        <div className="mt-4 grid grid-cols-2 gap-2">
                          <button type="button" onClick={() => setIsEmailModalOpen(true)} className="bg-slate-900 hover:bg-slate-800 text-slate-300 text-[10px] font-bold py-2 rounded border border-slate-800 flex items-center justify-center gap-1">Preview</button>
                          <a href={dispatchEmailData.mailtoLink} className="bg-amber-500 hover:bg-amber-400 text-slate-950 text-[10px] font-black py-2 rounded flex items-center justify-center gap-1 text-center font-bold">Send</a>
                        </div>
                      </div>
                    )}
                  </>
                )}

                {/* SAVE & RETURN BUTTON */}
                <div className="flex justify-end pb-8 pt-4">
                  <button 
                    onClick={() => setSelectedRowId(null)}
                    className="bg-emerald-600 hover:bg-emerald-500 text-white px-8 py-3 rounded-xl font-black text-sm tracking-wide shadow-lg shadow-emerald-900/20 flex items-center gap-2 transition"
                  >
                    <Save size={18} /> Save & Return to Summary
                  </button>
                </div>
              </div>

              {/* RIGHT COLUMN: UTILITY WIDGETS */}
              <div className="space-y-6">
                
                {/* DOCUMENT PRINT STATION */}
                <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg relative animate-fade-in">
                  <div className="absolute top-3 left-4 flex items-center space-x-1.5 text-slate-400">
                    <Printer size={13} className="text-amber-500" />
                    <span className="text-[9px] font-bold tracking-widest uppercase">Document Print Station</span>
                  </div>
                  
                  <div className="mt-8 space-y-2.5 w-full">
                    <button 
                      type="button" 
                      onClick={() => printCareDocument(selectedRecord)}
                      className="w-full bg-slate-900 hover:bg-slate-800 text-slate-200 border border-slate-800 text-xs font-semibold py-2.5 px-3 rounded-lg transition flex items-center justify-between"
                    >
                      <span className="flex items-center gap-2">
                        <Users size={14} className="text-amber-400" />
                        Print Care Form (Tab 1)
                      </span>
                      <Printer size={12} className="text-slate-500" />
                    </button>

                    <button 
                      type="button" 
                      onClick={() => printWorkshopDocument(selectedRecord)}
                      className="w-full bg-slate-900 hover:bg-slate-800 text-slate-200 border border-slate-800 text-xs font-semibold py-2.5 px-3 rounded-lg transition flex items-center justify-between"
                    >
                      <span className="flex items-center gap-2">
                        <Hammer size={14} className="text-amber-400" />
                        Print Workshop Spec (Tab 2)
                      </span>
                      <Printer size={12} className="text-slate-500" />
                    </button>

                    {selectedRecord?.isCoroner && (
                      <button 
                        type="button" 
                        onClick={() => printCoronerDocument(selectedRecord)}
                        className="w-full bg-slate-900 hover:bg-slate-800 text-slate-200 border border-slate-800 text-xs font-semibold py-2.5 px-3 rounded-lg transition flex items-center justify-between"
                      >
                        <span className="flex items-center gap-2">
                          <Truck size={14} className="text-rose-400" />
                          Print Coroner Dispatch (Tab 3)
                        </span>
                        <Printer size={12} className="text-slate-500" />
                      </button>
                    )}

                    <div className="pt-2 border-t border-slate-800/60">
                      <button 
                        type="button" 
                        onClick={() => printCombinedMasterDocument(selectedRecord)}
                        className="w-full bg-amber-500 hover:bg-amber-400 text-slate-950 text-xs font-black py-3 px-3 rounded-lg transition flex items-center justify-center gap-2 shadow-md shadow-amber-500/10"
                      >
                        <FileText size={14} />
                        Print Combined Master Record
                      </button>
                    </div>
                  </div>
                </div>

                {/* QR WIDGET */}
                <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 flex flex-col items-center text-center shadow-lg relative group">
                  <div className="absolute top-3 left-4 flex items-center space-x-1.5 text-slate-400"><QrCode size={13} className="text-amber-500" /><span className="text-[9px] font-bold tracking-widest uppercase">Tracking Pass</span></div>
                  <div className="mt-8 mb-4 bg-white p-3 rounded-lg shadow-inner">
                    <img src={getQrCodeUrl(selectedRecord, 140)} alt="QR Tracking" className="w-32 h-32 object-contain" />
                  </div>
                  <h4 className="text-xs font-black text-white uppercase flex items-center gap-1.5 justify-center"><span>Live File Link</span></h4>
                  
                  <div className="mt-5 w-full grid grid-cols-2 gap-2">
                    <button type="button" onClick={(e) => { e.preventDefault(); setIsQrModalOpen(true); }} className="bg-slate-900 hover:bg-slate-800 text-slate-300 text-[10px] font-bold py-2 rounded border border-slate-800 transition flex items-center justify-center gap-1.5"><Maximize2 size={12} /><span>Maximize</span></button>
                    <button type="button" onClick={(e) => { e.preventDefault(); printStickerAndCheckBlocks(selectedRecord); }} className="bg-amber-500 hover:bg-amber-400 text-slate-950 text-[10px] font-black py-2 rounded transition flex items-center justify-center gap-1.5 shadow-md"><Printer size={12} /><span>Sticker</span></button>
                  </div>
                </div>

                {/* ANATOMICAL SKULL CONDITION METRIC WIDGET */}
                {activeTab === "care" && (
                  <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 flex flex-col items-center text-center shadow-lg relative">
                    <span className="absolute top-3 left-4 text-[9px] font-black uppercase tracking-widest text-slate-500">Condition Metric</span>
                    <div className="my-6 p-4 bg-slate-900 rounded-full border border-slate-800 shadow-inner">
                      <BodyConditionIcon condition={selectedRecord?.condition} size={64} />
                    </div>
                    <h4 className="text-sm font-black text-white uppercase">Status: {selectedRecord?.condition}</h4>
                  </div>
                )}

                {/* FILE ADMINISTRATION CARD */}
                <div className="bg-slate-950 p-5 rounded-xl border border-slate-800 shadow-lg relative">
                  <div className="absolute top-3 left-4 flex items-center space-x-1.5 text-slate-400">
                    <FolderOpen size={13} className="text-amber-500" />
                    <span className="text-[9px] font-bold tracking-widest uppercase">File Administration</span>
                  </div>
                  
                  <div className="mt-8 space-y-2.5 w-full">
                    <button 
                      type="button" 
                      onClick={() => handleArchiveToggle(selectedRecord.id)}
                      className="w-full bg-slate-900 hover:bg-slate-800 text-slate-200 border border-slate-800 text-xs font-semibold py-2.5 px-3 rounded-lg transition flex items-center justify-between"
                    >
                      <span className="flex items-center gap-2">
                        <FolderOpen size={14} className="text-amber-400" />
                        {selectedRecord?.isArchived ? "Restore Case" : "Archive Custody Profile"}
                      </span>
                      <span className="text-[9px] text-slate-500 font-mono">STATUS</span>
                    </button>

                    <button 
                      type="button" 
                      onClick={() => confirmCaseDeletion(selectedRecord.id, selectedRecord.deceasedName)}
                      className="w-full bg-red-950/20 hover:bg-red-950/40 text-red-200 border border-red-900/40 text-xs font-semibold py-2.5 px-3 rounded-lg transition flex items-center justify-between"
                    >
                      <span className="flex items-center gap-2">
                        <Trash2 size={14} className="text-red-400" />
                        Delete Case Record
                      </span>
                      <span className="text-[9px] text-red-500 font-mono font-bold">DELETE</span>
                    </button>
                  </div>
                </div>

              </div>
            </div>
          </div>
        </div>
      )}

      {/* QR MAXIMIZE MODAL */}
      {isQrModalOpen && selectedRecord && (
        <div className="fixed inset-0 bg-black/90 backdrop-blur-sm flex items-center justify-center p-4 z-[9999]">
          <div className="bg-slate-950 border border-slate-800 rounded-2xl max-w-sm w-full p-6 text-center relative shadow-2xl animate-fade-in">
            <button onClick={() => setIsQrModalOpen(false)} className="absolute top-3 right-3 text-slate-400 hover:text-white p-1.5"><X size={18} /></button>
            <h3 className="text-base font-black text-white mt-2">{selectedRecord?.title} {selectedRecord?.deceasedName || "Unnamed"}</h3>
            <p className="text-[10px] text-slate-500 font-mono mt-0.5">Ref: {selectedRecord?.ref}</p>
            <div className="bg-white p-4 rounded-xl shadow-2xl inline-block my-4">
              <img src={getQrCodeUrl(selectedRecord, 220)} alt="High res QR" className="w-48 h-48 object-contain" />
            </div>
            <div className="mt-5 flex gap-2">
              <button onClick={() => { printStickerAndCheckBlocks(selectedRecord); setIsQrModalOpen(false); }} className="flex-1 bg-amber-500 text-slate-950 text-xs font-black py-2.5 rounded">Print Sticker</button>
              <button onClick={() => setIsQrModalOpen(false)} className="bg-slate-800 text-slate-300 text-xs font-bold px-5 py-2.5 rounded">Close</button>
            </div>
          </div>
        </div>
      )}

      {/* EMAIL PREVIEW LOGISTICS MODAL */}
      {isEmailModalOpen && selectedRecord && dispatchEmailData && (
        <div className="fixed inset-0 bg-black/90 flex items-center justify-center p-4 z-[9999]">
          <div className="bg-slate-950 border border-slate-800 rounded-2xl max-w-xl w-full p-6 relative shadow-2xl">
            <button onClick={() => setIsEmailModalOpen(false)} className="absolute top-3 right-3 text-slate-400 hover:text-white p-1.5"><X size={18} /></button>
            <h3 className="text-base font-black text-white mb-4">Email Preview</h3>
            <div className="space-y-2 bg-slate-900 p-4 rounded-xl border border-slate-800 text-xs font-mono">
              <div className="border-b border-slate-800 pb-2 text-slate-400"><span className="font-bold text-white">To:</span> {selectedRecord?.pickupStaffEmails}</div>
              <div className="border-b border-slate-800 pb-2 text-slate-400"><span className="font-bold text-white">Subject:</span> {dispatchEmailData.subject}</div>
              <div className="text-slate-300 whitespace-pre-wrap leading-relaxed max-h-64 overflow-y-auto pt-2">{dispatchEmailData.body}</div>
            </div>
            <div className="mt-5 flex gap-2 justify-end">
              <button onClick={() => setIsEmailModalOpen(false)} className="bg-slate-800 text-slate-300 text-xs font-bold px-4 py-2 rounded">Cancel</button>
              <a href={dispatchEmailData.mailtoLink} onClick={() => setIsEmailModalOpen(false)} className="bg-amber-500 text-slate-950 text-xs font-black px-5 py-2 rounded">Launch Client</a>
            </div>
          </div>
        </div>
      )}

      {/* SYSTEM CONFIRMATION MODAL */}
      {dialog.isOpen && (
        <div className="fixed inset-0 bg-black/80 backdrop-blur-sm flex items-center justify-center p-4 z-[9999]">
          <div className="bg-slate-950 border border-slate-800 rounded-xl p-6 max-w-sm w-full shadow-2xl space-y-4">
            <div className="flex items-center space-x-3 text-amber-500">
              <AlertTriangle className="flex-shrink-0" size={24} />
              <h4 className="text-base font-black uppercase tracking-wider text-white">{dialog.title}</h4>
            </div>
            <p className="text-xs text-slate-300 leading-relaxed">{dialog.message}</p>
            <div className="flex items-center justify-end space-x-2 pt-2">
              {dialog.type === "confirm" ? (
                <>
                  <button onClick={closeDialog} className="bg-slate-800 hover:bg-slate-700 text-slate-300 text-xs font-bold px-3 py-1.5 rounded transition">Cancel</button>
                  <button onClick={dialog.onConfirm} className="bg-red-600 hover:bg-red-500 text-white text-xs font-bold px-4 py-1.5 rounded transition">Confirm & Delete</button>
                </>
              ) : (
                <button onClick={closeDialog} className="bg-amber-500 hover:bg-amber-400 text-slate-950 text-xs font-bold px-4 py-1.5 rounded transition">Ok</button>
              )}
            </div>
          </div>
        </div>
      )}

    </div>
  );
}

function BodyConditionIcon({ condition, size = 32 }) {
  if (condition === 'Good') {
    return (
      <svg width={size} height={size} viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" className="text-emerald-400">
        <circle cx="50" cy="50" r="46" stroke="currentColor" strokeWidth="4" className="opacity-30" />
        <path d="M50 18C32.32 18 18 32.32 18 50C18 64.6 27.84 76.92 41.25 80.7C42.84 81.15 44 82.59 44 84.25V87C44 88.66 45.34 90 47 90H53C54.66 90 56 88.66 56 87V84.25C56 82.59 57.16 81.15 58.75 80.7C72.16 76.92 82 64.6 82 50C82 32.32 67.68 18 50 18Z" stroke="currentColor" strokeWidth="4" strokeLinecap="round" />
        <path d="M32 46C35 49 41 49 44 46" stroke="currentColor" strokeWidth="4" strokeLinecap="round" />
        <path d="M56 46C59 49 65 49 68 46" stroke="currentColor" strokeWidth="4" strokeLinecap="round" />
        <path d="M42 66C45 68 55 68 58 66" stroke="currentColor" strokeWidth="3" strokeLinecap="round" />
        <circle cx="28" cy="56" r="3" fill="currentColor" fillOpacity="0.3" />
        <circle cx="72" cy="56" r="3" fill="currentColor" fillOpacity="0.3" />
      </svg>
    );
  } else if (condition === 'Medium') {
    return (
      <svg width={size} height={size} viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" className="text-amber-400">
        <circle cx="50" cy="50" r="46" stroke="currentColor" strokeWidth="4" className="opacity-30" />
        <path d="M50 18C34 18 20 32 20 48C20 60 26 70 34 75.5C36 76.8 38 78 38 80.5V85C38 86.6 39.4 88 41 88H59C60.6 88 62 86.6 62 85V80.5C62 78 64 76.8 66 75.5C74 70 80 60 80 48C80 32 66 18 50 18Z" stroke="currentColor" strokeWidth="4" strokeLinecap="round" />
        <path d="M28 44C28 41 38 41 38 44C38 47 28 47 28 44Z" stroke="currentColor" strokeWidth="2.5" strokeLinecap="round" fill="currentColor" fillOpacity="0.1" />
        <path d="M62 44C62 41 72 41 72 44C72 47 62 47 62 44Z" stroke="currentColor" strokeWidth="2.5" strokeLinecap="round" fill="currentColor" fillOpacity="0.1" />
        <line x1="30" y1="44" x2="36" y2="44" stroke="currentColor" strokeWidth="3" strokeLinecap="round" />
        <line x1="64" y1="44" x2="70" y2="44" stroke="currentColor" strokeWidth="3" strokeLinecap="round" />
        <line x1="44" y1="64" x2="56" y2="64" stroke="currentColor" strokeWidth="3" strokeLinecap="round" />
        <path d="M24 58C28 61 28 65 26 69" stroke="currentColor" strokeWidth="2" strokeLinecap="round" />
        <path d="M76 58C72 61 72 65 74 69" stroke="currentColor" strokeWidth="2" strokeLinecap="round" />
      </svg>
    );
  } else {
    // Severe condition skull SVG
    return (
      <svg width={size} height={size} viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" className="text-red-500">
        <circle cx="50" cy="50" r="46" stroke="currentColor" strokeWidth="4" className="opacity-30" />
        <path d="M50 14C28 14 22 28 22 48C22 55.5 25.5 60.5 29 63.5C31.5 66.5 33 67 33 71V79C33 83.5 36.5 86 41 86H59C63.5 86 67 83.5 67 79V71C67 67 68.5 66.5 71 63.5C74.5 60.5 78 55.5 78 48C78 28 72 14 50 14Z" stroke="currentColor" strokeWidth="4" strokeLinejoin="round" />
        <circle cx="36" cy="45" r="10" stroke="currentColor" strokeWidth="4" fill="currentColor" fillOpacity="0.3" />
        <circle cx="64" cy="45" r="10" stroke="currentColor" strokeWidth="4" fill="currentColor" fillOpacity="0.3" />
        <path d="M50 52L46 60H54L50 52Z" stroke="currentColor" strokeWidth="3.5" fill="currentColor" />
        <path d="M37 75H63" stroke="currentColor" strokeWidth="4" strokeLinecap="round" />
        <line x1="43" y1="71" x2="43" y2="79" stroke="currentColor" strokeWidth="3.5" strokeLinecap="round" />
        <line x1="50" y1="71" x2="50" y2="79" stroke="currentColor" strokeWidth="3.5" strokeLinecap="round" />
        <line x1="57" y1="71" x2="57" y2="79" stroke="currentColor" strokeWidth="3.5" strokeLinecap="round" />
        <path d="M26 30C24 35 24 38 26 41" stroke="currentColor" strokeWidth="2" strokeLinecap="round" />
        <path d="M74 30C76 35 76 38 74 41" stroke="currentColor" strokeWidth="2" strokeLinecap="round" />
      </svg>
    );
  }
}