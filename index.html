import React, { useState, useEffect, useRef, useMemo } from 'react';
import { LayoutDashboard, BookOpen, Users, Calendar, ClipboardCheck, GraduationCap, FileText, Settings, Menu, X, Plus, Save, Trash2, Search, CheckCircle, BarChart3, UserCheck, Database, Edit, School, MoreVertical, Key, LogOut, Lock, UserCog, Sun, LogIn, Eye, EyeOff, XCircle, Download, Clock, MapPin, Activity, Crosshair, AlertCircle, Upload, FileSpreadsheet, Book, Folder, File, Link, Wifi, BrainCircuit, FileBadge, Loader2 } from 'lucide-react';
import { initializeApp } from 'firebase/app';
import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from 'firebase/auth';
import { getFirestore, doc, setDoc, onSnapshot } from 'firebase/firestore';

// --- FIREBASE INITIALIZATION ---
const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
    apiKey: "AIzaSyBddZVSGYw-D-8qvPd-My8c3mMDWo_OZSA",
    authDomain: "jurnalaltaz.firebaseapp.com",
    projectId: "jurnalaltaz",
    storageBucket: "jurnalaltaz.firebasestorage.app",
    messagingSenderId: "658444272373",
    appId: "1:658444272373:web:909b7a424bbf7aaa763bbc"
};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);
const globalAppId = typeof __app_id !== 'undefined' ? __app_id : 'jurnalaltaz';

// --- DATA MOCKUP AWAL ---
const INITIAL_STUDENTS = [
    { id: 1, name: 'Ahmad Dahlan', nis: '2024001', gender: 'L', class: 'X-A', status: 'Aktif' },
    { id: 2, name: 'Budi Santoso', nis: '2024002', gender: 'L', class: 'X-A', status: 'Aktif' },
];
const INITIAL_TEACHERS = [
    { id: 1, name: 'Bpk. Guru RI', nip: '198501012010011001', mapel: 'Matematika', status: 'Wali Kelas, Guru Piket' }, 
    { id: 4, name: 'Bpk. Kepala Sekolah', nip: '198001012005011001', mapel: 'PKN', status: 'Kepala Sekolah' },
];
const INITIAL_CLASSES = [{ id: 'X-A', name: 'X-A', wali: 'Bpk. Guru RI', total: 32 }];
const INITIAL_SUBJECTS = [{ id: 1, code: 'MTK-E', name: 'Matematika', kktp: '75' }];
const INITIAL_SCHEDULE = [{ id: 1, day: 'Senin', jamKe: '1-2', time: '07:10 - 08:30', class: 'X-A', subject: 'Matematika', room: 'R. 101', teacherName: 'Bpk. Guru RI' }];
const INITIAL_ACCOUNTS = [
    { username: 'admin', password: '123', role: 'admin', name: 'Administrator Sekolah' },
    { username: 'guru', password: '123', role: 'guru', name: 'Bpk. Guru RI', teacherId: 1 },
];
const INITIAL_DRIVE_LINKS = { 1: { perangkat: 'https://drive.google.com/', sas_sat: '', psaj: '' } };
const INITIAL_SCHOOL_DOCS = { sk_kbm: '', pekan_efektif: '' };
const INITIAL_SCHOOL_CONFIG = { name: 'SMA Negeri 1 Edukasi', npsn: '12345678', level: 'SMA/MA', logo: 'https://ui-avatars.com/api/?name=SM&background=4f46e5&color=fff&size=128', academicYear: '2025/2026', semester: 'Ganjil', address: 'Jl. Pendidikan No. 1, Kec. Ilmu, Kota Pelajar', email: 'info@sman1edukasi.sch.id' };

const generateId = () => Date.now().toString(36) + Math.random().toString(36).substr(2, 9);

// --- FUNGSI PENGHITUNG WAKTU OTOMATIS ---
const calculateJamTime = (jamKeString) => {
    if (!jamKeString) return '';
    const parts = jamKeString.toString().split('-');
    const startJam = parseInt(parts[0]);
    const endJam = parts.length > 1 ? parseInt(parts[1]) : startJam;

    if (isNaN(startJam) || isNaN(endJam)) return jamKeString;

    const getMinsCorrected = (jam, isEnd) => {
        let mins = 430 + (jam - 1) * 40; // 07:10 dimulai pada menit ke-430
        if (isEnd) mins += 40;
        // Jika Jam lebih dari 5, tambahkan 20 menit untuk istirahat (10.30 - 10.50)
        if (!isEnd && jam > 5) mins += 20; 
        if (isEnd && jam > 5) mins += 20;
        return mins;
    };

    const format = (mins) => `${Math.floor(mins/60).toString().padStart(2,'0')}:${(mins%60).toString().padStart(2,'0')}`;
    return `${format(getMinsCorrected(startJam, false))} - ${format(getMinsCorrected(endJam, true))}`;
};

// --- HOOK FIREBASE AMAN (ANTI RESET) ---
const useFirebaseData = (docId, initialValue, fbUser, onLoaded) => {
    const [data, setData] = useState(initialValue);
    const [loading, setLoading] = useState(true);
    const dataRef = useRef(data);
    const hasLoadedInitial = useRef(false);

    useEffect(() => {
        dataRef.current = data;
    }, [data]);

    useEffect(() => {
        if (!fbUser) return;
        const docRef = doc(db, 'artifacts', globalAppId, 'public', 'data', 'master_data', docId);
        const unsubscribe = onSnapshot(docRef, (snap) => {
            if (snap.exists()) {
                setData(snap.data().items || initialValue);
            } else {
                // Hanya gunakan initialValue jika ini adalah muat pertama dan dokumen benar-benar tidak ada di database
                if (!hasLoadedInitial.current) {
                    setData(initialValue);
                }
            }
            
            if (!hasLoadedInitial.current) {
                hasLoadedInitial.current = true;
                setLoading(false);
                if (onLoaded) onLoaded(); // Beritahu App bahwa data ini selesai dimuat
            }
        }, (err) => {
            console.error(`Firebase Sync Error on ${docId}:`, err);
            // JANGAN mengubah data menjadi initialValue saat error koneksi, biarkan cache memori (data saat ini) yang berjalan.
            if (!hasLoadedInitial.current) {
                 setLoading(false);
                 if (onLoaded) onLoaded();
            }
        });
        return () => unsubscribe();
    }, [fbUser, docId]); // initialValue dan onLoaded tidak menjadi dependensi agar tidak me-reset efek

    const saveData = async (newDataAction) => {
        if (!fbUser) return;
        try {
            const valueToStore = typeof newDataAction === 'function' ? newDataAction(dataRef.current) : newDataAction;
            setData(valueToStore); // Perbarui tampilan dengan seketika
            const docRef = doc(db, 'artifacts', globalAppId, 'public', 'data', 'master_data', docId);
            await setDoc(docRef, { items: valueToStore }, { merge: true }); // Simpan ke database
        } catch (error) {
            console.error("Failed to save:", error);
            throw error;
        }
    };

    return [data, saveData, loading];
};

// --- KOMPONEN BERSAMA ---
const ToastContainer = ({ toast }) => {
    if (!toast) return null;
    return (
        <div className="fixed top-4 right-4 z-[70] animate-fade-in-down w-full max-w-sm px-4 md:w-auto md:px-0">
            <div className={`flex items-center gap-3 px-6 py-4 rounded-xl shadow-2xl text-white ${toast.type === 'error' ? 'bg-red-600' : 'bg-slate-800'}`}>
                {toast.type === 'error' ? <AlertCircle size={20} className="text-white" /> : <CheckCircle size={20} className="text-emerald-400" />}
                <span className="font-medium text-sm md:text-base">{toast.message}</span>
            </div>
        </div>
    );
};

const ConfirmModal = ({ confirm }) => {
    if (!confirm) return null;
    return (
        <div className="fixed inset-0 z-[60] flex items-center justify-center modal-overlay p-4">
            <div className="bg-white rounded-2xl shadow-2xl p-6 md:p-8 max-w-sm w-full animate-fade-in-down">
                <div className="flex flex-col items-center text-center mb-6">
                    <div className="w-16 h-16 bg-orange-100 text-orange-600 rounded-full flex items-center justify-center mb-4"><AlertCircle size={32} /></div>
                    <h3 className="text-xl font-bold text-slate-800 mb-2">Konfirmasi</h3>
                    <p className="text-slate-600 text-sm md:text-base">{confirm.message}</p>
                </div>
                <div className="flex gap-3">
                    <button onClick={confirm.onCancel} className="flex-1 py-3 bg-slate-100 text-slate-700 font-bold rounded-xl hover:bg-slate-200 transition-colors">Batal</button>
                    <button onClick={confirm.onConfirm} className="flex-1 py-3 bg-indigo-600 text-white font-bold rounded-xl hover:bg-indigo-700 transition-colors">Ya, Lanjutkan</button>
                </div>
            </div>
        </div>
    );
};

const StatCard = ({ title, value, icon: Icon, color }) => (
    <div className="bg-white p-6 rounded-2xl shadow-sm border border-slate-100 flex items-start justify-between hover:shadow-md transition-shadow">
        <div>
            <p className="text-sm font-medium text-slate-500">{title}</p>
            <h3 className="text-3xl font-bold text-slate-800 mt-2">{value}</h3>
        </div>
        <div className={`p-4 rounded-xl ${color} shadow-sm transform rotate-3`}>
            <Icon size={28} className="text-white" />
        </div>
    </div>
);

const JurnalKokurikuler = ({ showToast }) => (
    <div className="flex flex-col items-center justify-center py-20 bg-white rounded-2xl border border-dashed border-slate-300">
        <div className="bg-indigo-50 p-4 rounded-full mb-4">
            <GraduationCap size={40} className="text-indigo-600" />
        </div>
        <h3 className="text-xl font-bold text-slate-800">Fitur Jurnal P5 (Kokurikuler)</h3>
        <p className="text-slate-500 mt-2">Modul ini sedang dalam tahap pengembangan.</p>
    </div>
);

const DokumenView = ({ title, type, schoolDocs }) => {
    return (
        <div className="bg-white p-8 rounded-2xl border border-slate-200 shadow-sm animate-fade-in text-center">
            <div className="w-16 h-16 bg-blue-50 text-blue-600 rounded-full flex items-center justify-center mx-auto mb-4">
                <FileText size={32} />
            </div>
            <h2 className="text-xl font-bold text-slate-800 mb-2">{title}</h2>
            {schoolDocs && schoolDocs[type] ? (
                <div className="mt-4">
                    <a href={schoolDocs[type]} target="_blank" rel="noreferrer" className="inline-flex items-center gap-2 px-6 py-3 bg-blue-600 text-white rounded-xl font-bold hover:bg-blue-700 transition-colors">
                        <Download size={18} /> Unduh / Lihat Dokumen
                    </a>
                </div>
            ) : (
                <p className="text-slate-500 mt-2">Dokumen belum diunggah oleh admin.</p>
            )}
        </div>
    );
};

// --- LAYAR LOGIN ---
const LoginScreen = ({ onLogin, accounts, showToast, schoolConfig }) => {
    const [username, setUsername] = useState('');
    const [password, setPassword] = useState('');
    const [showPassword, setShowPassword] = useState(false);
    const [error, setError] = useState('');

    const handleSubmit = (e) => {
        e.preventDefault();
        let foundAccount = (accounts || []).find(acc => acc.username === username && acc.password === password);
        if (foundAccount) {
            let sessionUser = { ...foundAccount };
            if (sessionUser.role === 'guru') {
                if (sessionUser.teacherId) sessionUser.id = sessionUser.teacherId;
                else if (!sessionUser.id) sessionUser.id = 1;
            }
            onLogin(sessionUser);
        } else {
            setError('Username atau Password salah!');
            showToast('Login Gagal: Periksa username dan password', 'error');
        }
    };

    return (
        <div className="min-h-screen bg-gradient-to-br from-indigo-500 via-purple-500 to-pink-500 flex items-center justify-center p-4 font-sans selection:bg-indigo-100 selection:text-indigo-700">
            <div className="bg-white w-full max-w-md rounded-2xl shadow-2xl overflow-hidden transform hover:scale-[1.01] transition-transform duration-300 mx-auto">
                <div className="bg-gradient-to-r from-indigo-600 to-purple-600 p-8 md:p-10 text-center relative overflow-hidden">
                    <div className="absolute top-0 left-0 w-full h-full bg-white/10 opacity-20 transform -skew-y-6 scale-150 origin-bottom-left"></div>
                    <div className="w-16 h-16 md:w-20 md:h-20 bg-white/20 rounded-2xl flex items-center justify-center mx-auto mb-4 backdrop-blur-md shadow-inner relative z-10 overflow-hidden">
                        {schoolConfig?.logo ? <img src={schoolConfig.logo} alt="Logo" className="w-full h-full object-cover" /> : <School size={40} className="text-white drop-shadow-md" />}
                    </div>
                    <h1 className="text-2xl md:text-3xl font-bold text-white relative z-10 tracking-tight">{schoolConfig?.name || 'SIJAGA'}</h1>
                    <p className="text-indigo-100 text-[10px] md:text-xs mt-1 relative z-10 font-medium opacity-90">(Sistem Jurnal dan Administrasi Guru Mengajar)</p>
                </div>
                
                <div className="p-6 md:p-8 pt-8 md:pt-10">
                    <form onSubmit={handleSubmit} className="space-y-5 md:space-y-6">
                        <div>
                            <label className="block text-sm font-semibold text-slate-700 mb-2 ml-1">Username / NIP</label>
                            <div className="relative group">
                                <div className="absolute left-0 top-0 bottom-0 w-12 flex items-center justify-center text-slate-400 group-focus-within:text-indigo-500 transition-colors pointer-events-none"><Users size={20} /></div>
                                <input type="text" value={username} onChange={(e) => setUsername(e.target.value)} className="w-full pl-12 pr-4 py-3.5 border border-slate-200 rounded-xl focus:ring-2 focus:ring-indigo-500/30 focus:border-indigo-500 outline-none transition-all bg-slate-50 focus:bg-white placeholder-slate-400 text-slate-800 font-medium" placeholder="Masukkan username" />
                            </div>
                        </div>
                        <div>
                            <label className="block text-sm font-semibold text-slate-700 mb-2 ml-1">Password</label>
                            <div className="relative group">
                                <div className="absolute left-0 top-0 bottom-0 w-12 flex items-center justify-center text-slate-400 group-focus-within:text-indigo-500 transition-colors pointer-events-none"><Lock size={20} /></div>
                                <input type={showPassword ? "text" : "password"} value={password} onChange={(e) => setPassword(e.target.value)} className="w-full pl-12 pr-12 py-3.5 border border-slate-200 rounded-xl focus:ring-2 focus:ring-indigo-500/30 focus:border-indigo-500 outline-none transition-all bg-slate-50 focus:bg-white placeholder-slate-400 text-slate-800 font-medium" placeholder="Masukkan password" />
                                <button type="button" onClick={() => setShowPassword(!showPassword)} className="absolute right-0 top-0 bottom-0 w-12 flex items-center justify-center text-slate-400 hover:text-indigo-600 transition-colors focus:outline-none">{showPassword ? <EyeOff size={18} /> : <Eye size={18} />}</button>
                            </div>
                        </div>
                        {error && (
                            <div className="p-4 bg-red-50 border border-red-100 text-red-600 text-sm rounded-xl flex items-center gap-3 animate-fade-in">
                                <div className="bg-red-100 p-1.5 rounded-full text-red-600"><X size={16} /></div> 
                                <span className="font-medium">{error}</span>
                            </div>
                        )}
                        <button type="submit" className="w-full bg-gradient-to-r from-indigo-600 to-purple-600 hover:from-indigo-700 hover:to-purple-700 text-white py-3.5 rounded-xl font-bold transition-all shadow-lg shadow-indigo-200 hover:shadow-indigo-300 transform hover:-translate-y-0.5 active:translate-y-0 flex items-center justify-center gap-2">
                            <LogIn size={20} /> Masuk Aplikasi
                        </button>
                    </form>
                </div>
            </div>
        </div>
    );
};

// --- KOMPONEN SIDEBAR ---
const Sidebar = ({ activeTab, setActiveTab, isOpen, setIsOpen, user, onLogout, isPiket, isManagement, isWaliKelas, schoolConfig }) => {
    const [isHovered, setIsHovered] = useState(false);
    const menuGroups = [
        { category: "Menu Utama", items: [{ id: 'dashboard', label: 'Dashboard', icon: LayoutDashboard, roles: ['admin', 'guru'] }, { id: 'monitoring', label: 'Monitoring Guru', icon: Activity, roles: ['admin'] }, { id: 'analisis-siswa', label: 'Analisis Siswa', icon: BrainCircuit, roles: ['admin'] }, { id: 'data', label: 'Manajemen Data', icon: Database, roles: ['admin'] }, { id: 'generate-akun', label: 'Generate Akun', icon: Key, roles: ['admin'] }] },
        { category: "Administrasi Guru", items: [{ id: 'absensi-guru', label: 'Absensi Saya', icon: MapPin, roles: ['guru'] }, { id: 'jadwal', label: 'Jadwal Mengajar', icon: Calendar, roles: ['guru'] }, { id: 'jurnal', label: 'Jurnal Mengajar', icon: Book, roles: ['guru'] }, { id: 'presensi', label: 'Presensi Siswa', icon: UserCheck, roles: ['guru'] }, { id: 'asesmen', label: 'Asesmen & Nilai', icon: ClipboardCheck, roles: ['guru'] }, { id: 'drive-guru', label: 'Drive Administrasi', icon: Folder, roles: ['guru'] }] },
        { category: "Tugas Tambahan", items: [{ id: 'jurnal-piket', label: 'Jurnal Piket', icon: ClipboardCheck, roles: ['guru'] }] }
    ];

    const isExpanded = isOpen || isHovered; 
    return (
        <>
            <div className={`fixed inset-0 bg-slate-900/50 z-40 md:hidden transition-opacity duration-300 ${isOpen ? 'opacity-100' : 'opacity-0 pointer-events-none'}`} onClick={() => setIsOpen(false)}></div>
            <div className={`fixed md:relative inset-y-0 left-0 z-50 bg-slate-900 text-white sidebar-transition flex flex-col shadow-2xl md:shadow-none overflow-hidden ${isOpen ? 'translate-x-0 w-64' : '-translate-x-full md:translate-x-0'} md:w-20 hover:md:w-64`} onMouseEnter={() => setIsHovered(true)} onMouseLeave={() => setIsHovered(false)}>
                <div className="flex flex-col justify-center h-20 px-6 bg-slate-950 border-b border-slate-800 shrink-0">
                    <div className="flex items-center gap-3 font-bold text-xl tracking-tight text-white">
                        <div className="w-8 h-8 bg-white rounded-lg flex items-center justify-center shadow-lg overflow-hidden shrink-0">
                            {schoolConfig?.logo ? <img src={schoolConfig.logo} alt="Logo" className="w-full h-full object-cover" /> : <School size={20} className="text-indigo-600" />}
                        </div>
                        <span className={`whitespace-nowrap transition-opacity duration-300 ${isExpanded ? 'opacity-100 delay-100' : 'opacity-0 md:hidden'}`}>SIJAGA</span>
                        <button onClick={() => setIsOpen(false)} className="md:hidden text-slate-400 hover:text-white ml-auto"><X size={24} /></button>
                    </div>
                </div>
                
                <div className="flex-1 px-3 py-6 overflow-y-auto no-scrollbar overflow-x-hidden">
                    {menuGroups.map((group, idx) => {
                        const visibleItems = group.items.filter(item => {
                            if (item.id === 'jurnal-piket') return isPiket;
                            if (item.id === 'monitoring') return isManagement; 
                            if (item.id === 'analisis-siswa') return (user.role === 'admin' || isManagement || isWaliKelas);
                            return item.roles.includes(user.role);
                        });
                        if (visibleItems.length === 0) return null;
                        return (
                            <div key={idx} className="mb-6">
                                <div className={`mb-2 px-4 transition-opacity duration-300 ${isExpanded ? 'opacity-100' : 'opacity-0 md:hidden'}`}><p className="text-[10px] text-slate-500 uppercase font-bold tracking-widest whitespace-nowrap">{group.category}</p></div>
                                <nav className="space-y-1.5">
                                    {visibleItems.map((item) => (
                                        <button key={item.id} onClick={() => { 
                                            if (item.id === 'asesmen') {
                                                window.open('https://erapor-zeta.vercel.app/', '_blank');
                                            } else if (item.id === 'jurnal-piket') {
                                                window.open('https://sigapaltaz.web.app/', '_blank');
                                            } else {
                                                setActiveTab(item.id); 
                                                setIsOpen(false); 
                                            }
                                        }} className={`w-full flex items-center gap-3 px-3 py-3 text-sm font-medium rounded-xl transition-all duration-200 group relative overflow-hidden ${activeTab === item.id ? 'bg-indigo-600 text-white shadow-lg shadow-indigo-900/30' : 'text-slate-400 hover:bg-slate-800 hover:text-white'}`} title={!isExpanded ? item.label : ''}>
                                            <item.icon size={22} className={`shrink-0 transition-colors ${activeTab === item.id ? "text-white" : "text-slate-500 group-hover:text-white"}`} />
                                            <span className={`whitespace-nowrap transition-all duration-300 ${isExpanded ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-4 absolute left-12'}`}>{item.label}</span>
                                        </button>
                                    ))}
                                </nav>
                            </div>
                        );
                    })}
                </div>
                <div className="p-3 bg-slate-950 border-t border-slate-800 shrink-0">
                    <button onClick={onLogout} className={`w-full flex items-center gap-2 py-3 bg-slate-800 hover:bg-red-600/90 text-slate-300 hover:text-white rounded-lg text-xs font-bold transition-all uppercase tracking-wide group ${isExpanded ? 'justify-start px-4' : 'justify-center px-0'}`} title="Keluar">
                        <LogOut size={16} className="group-hover:-translate-x-0.5 transition-transform" /> <span className={`transition-all duration-300 ${isExpanded ? 'opacity-100 ml-1' : 'opacity-0 w-0 overflow-hidden'}`}>Keluar</span>
                    </button>
                </div>
            </div>
        </>
    );
};

// --- KOMPONEN FITUR UTAMA ---
const Dashboard = ({ user, teachersCount, studentsCount, setActiveTab, classLogs, setClassLogs, teacherAttendance, schedules, jurnals, showToast, isManagement }) => {
    const today = new Date();
    const todayISO = today.toISOString().split('T')[0];
    const todayLocale = today.toLocaleDateString('id-ID');
    const days = ['Minggu', 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'];
    const activeDay = days[today.getDay()];
    let pendingTasks = [];
    
    const handleMasukKelas = (schedule) => {
        const newLog = {
            id: Date.now(),
            teacherName: user.name,
            className: schedule.class,
            subject: schedule.subject,
            time: new Date().toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit' }),
            scheduleId: schedule.id,
            date: todayISO
        };
        setClassLogs((prev) => [newLog, ...(prev || [])]);
        showToast(`Berhasil masuk kelas ${schedule.class} - ${schedule.subject}`);
    };

    if (user && user.role === 'guru') {
        const hasAbsensi = (teacherAttendance || []).some(t => t.teacherName === user.name && t.date === todayISO);
        if (!hasAbsensi) {
            pendingTasks.push({ id: 'absen-pagi', title: 'Absensi Kehadiran Sekolah', desc: 'Anda belum mencatat kehadiran datang hari ini.', type: 'urgent', link: 'absensi-guru', btnText: 'Absen Sekarang' });
        }
        const mySchedulesToday = (schedules || []).filter(s => s.day === activeDay && s.teacherName === user.name);
        mySchedulesToday.forEach(sch => {
            const hasEntered = (classLogs || []).some(log => log.scheduleId === sch.id && log.date === todayISO);
            if (!hasEntered) {
                pendingTasks.push({ 
                    id: `masuk-${sch.id}`, 
                    title: `Masuk Kelas ${sch.class}`, 
                    desc: `${sch.subject} (${sch.time || '00:00'})`, 
                    type: 'warning', 
                    btnText: 'Masuk Kelas',
                    action: () => handleMasukKelas(sch) 
                });
            }
            const hasJournal = (jurnals || []).some(j => j.scheduleId === sch.id && j.date === todayLocale);
            if (!hasJournal) {
                pendingTasks.push({ id: `jurnal-${sch.id}`, title: `Isi Jurnal ${sch.class}`, desc: `${sch.subject} - ${sch.time || '00:00'}`, type: 'info', link: 'jurnal', btnText: 'Isi Jurnal' });
            }
        });
    }

    return (
        <div className="space-y-8 animate-fade-in">
            <div className="flex flex-col md:flex-row md:items-center justify-between gap-4 bg-white p-6 rounded-2xl border border-slate-100 shadow-sm">
                <div className="flex items-center gap-4">
                    <div className="p-3 bg-orange-100 text-orange-600 rounded-full"><Sun size={32} /></div>
                    <div>
                        <h1 className="text-2xl font-bold text-slate-800">Selamat Pagi, {user.name}!</h1>
                        <p className="text-slate-500">{isManagement && user.role !== 'admin' ? 'Panel Kepala Sekolah / Manajemen.' : user.role === 'admin' ? 'Panel Administrator Sekolah SIJAGA.' : `Semangat mengajar di hari ${activeDay} ini!`}</p>
                    </div>
                </div>
                <div className="bg-indigo-50 text-indigo-700 px-5 py-3 rounded-xl text-sm font-bold border border-indigo-100 flex items-center gap-2"><Calendar size={18} /> {today.toLocaleDateString('id-ID', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}</div>
            </div>
            {user.role === 'guru' && !isManagement && (
                <div className={`rounded-2xl shadow-sm overflow-hidden animate-fade-in-down border ${pendingTasks.length > 0 ? 'bg-white border-red-100' : 'bg-emerald-50 border-emerald-100'}`}>
                    <div className={`p-4 border-b flex items-center gap-2 ${pendingTasks.length > 0 ? 'bg-red-50/50 border-red-100' : 'bg-emerald-100/50 border-emerald-200'}`}>{pendingTasks.length > 0 ? <AlertCircle size={20} className="text-red-500" /> : <CheckCircle size={20} className="text-emerald-500" />}<h3 className={`font-bold ${pendingTasks.length > 0 ? 'text-red-700' : 'text-emerald-700'}`}>{pendingTasks.length > 0 ? `Daftar Pekerjaan Belum Selesai (${pendingTasks.length})` : 'Semua Pekerjaan Hari Ini Selesai!'}</h3></div>
                    {pendingTasks.length > 0 ? (
                        <div className="divide-y divide-slate-100">
                            {pendingTasks.map((task) => (
                                <div key={task.id} className="p-4 flex flex-col md:flex-row md:items-center justify-between hover:bg-slate-50 transition-colors gap-3"><div className="flex items-start gap-3"><div className={`w-2 h-2 rounded-full mt-2 flex-shrink-0 ${task.type === 'urgent' ? 'bg-red-500' : task.type === 'warning' ? 'bg-orange-500' : 'bg-blue-500'}`}></div><div><span className="font-bold text-slate-700 block">{task.title}</span>{task.desc && <span className="text-xs text-slate-500">{task.desc}</span>}</div></div><button onClick={() => task.action ? task.action() : setActiveTab(task.link)} className="px-4 py-2 text-xs font-bold bg-white border border-slate-200 text-slate-600 rounded-xl hover:bg-indigo-50 hover:text-indigo-600 hover:border-indigo-200 transition-all shadow-sm whitespace-nowrap">{task.btnText}</button></div>
                            ))}
                        </div>
                    ) : (
                        <div className="p-6 text-center text-emerald-600 text-sm font-medium">Luar biasa! Anda telah menyelesaikan semua administrasi mengajar untuk hari ini.</div>
                    )}
                </div>
            )}
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <StatCard title="Total Siswa" value={studentsCount} icon={Users} color="bg-gradient-to-br from-blue-500 to-blue-600" />
                <StatCard title="Total Guru" value={teachersCount} icon={UserCog} color="bg-gradient-to-br from-pink-500 to-pink-600" />
                <StatCard title="Total Kelas" value="5" icon={LayoutDashboard} color="bg-gradient-to-br from-emerald-500 to-emerald-600" />
                {user.role === 'guru' && <StatCard title="Jam Mengajar" value="24 JP" icon={Calendar} color="bg-gradient-to-br from-orange-500 to-orange-600" />}
            </div>
            {user.role === 'guru' && (
                <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    <div className="lg:col-span-2 bg-white p-8 rounded-2xl shadow-sm border border-slate-100">
                        <h3 className="font-bold text-xl text-slate-800 mb-6 flex items-center gap-3"><div className="p-2 bg-indigo-100 text-indigo-600 rounded-lg"><Calendar size={24} /></div> Jadwal Hari Ini ({activeDay})</h3>
                        <div className="space-y-4">
                            {(schedules || []).filter(s => s.day === activeDay).length > 0 ? (
                                (schedules || []).filter(s => s.day === activeDay).map((item, idx) => {
                                    const isEntered = (classLogs || []).some(log => log.scheduleId === item.id && log.date === todayISO);
                                    return (
                                        <div key={`${item.id}-${idx}`} className="flex items-center p-5 bg-slate-50 rounded-xl border border-slate-100 hover:border-indigo-300 transition-colors group">
                                            <div className="w-16 text-center"><span className="block text-xs font-bold text-slate-400 uppercase tracking-wider">Jam</span><span className="text-lg font-bold text-indigo-600">{item.jamKe || (item.time || '').split(' - ')[0] || '--:--'}</span></div>
                                            <div className="h-12 w-px bg-slate-200 mx-6"></div>
                                            <div>
                                                <h4 className="font-bold text-lg text-slate-800 group-hover:text-indigo-700 transition-colors">{item.subject}</h4>
                                                <p className="text-sm text-slate-500 flex items-center gap-2 mt-1"><Users size={14} /> Kelas {item.class} • Ruang {item.room} <br/><span className="text-xs text-slate-400 font-normal">Guru: {item.teacherName}</span></p>
                                            </div>
                                            <div className="ml-auto">
                                                {isEntered ? (
                                                    <span className="px-4 py-2 bg-emerald-100 text-emerald-700 text-sm font-bold rounded-lg flex items-center gap-2"><CheckCircle size={14} /> Di Kelas</span>
                                                ) : (
                                                    item.teacherName === user.name && (
                                                        <button onClick={() => handleMasukKelas(item)} className="px-4 py-2 bg-white border border-indigo-200 text-indigo-600 text-sm font-bold rounded-lg hover:bg-indigo-600 hover:text-white transition-all shadow-sm flex items-center gap-2"><LogIn size={14} /> Masuk Kelas</button>
                                                    )
                                                )}
                                            </div>
                                        </div>
                                    );
                                })
                            ) : (<div className="text-center py-8 text-slate-400 bg-slate-50 rounded-xl border border-dashed border-slate-200">Tidak ada jadwal pelajaran di sekolah hari ini.</div>)}
                        </div>
                    </div>
                    <div className="bg-white p-8 rounded-2xl shadow-sm border border-slate-100">
                        <h3 className="font-bold text-xl text-slate-800 mb-6">Aktivitas Cepat</h3>
                        <div className="grid grid-cols-2 gap-4">
                            <button onClick={() => window.open('https://erapor-zeta.vercel.app/', '_blank')} className="p-5 bg-blue-50 text-blue-700 rounded-2xl text-sm font-bold hover:bg-blue-100 flex flex-col items-center gap-3 border border-blue-100 transition-transform hover:scale-105"><div className="p-3 bg-white rounded-full shadow-sm"><Plus size={24} /></div>Input Nilai</button>
                            <button onClick={() => setActiveTab('presensi')} className="p-5 bg-emerald-50 text-emerald-700 rounded-2xl text-sm font-bold hover:bg-emerald-100 flex flex-col items-center gap-3 border border-emerald-100 transition-transform hover:scale-105"><div className="p-3 bg-white rounded-full shadow-sm"><UserCheck size={24} /></div>Presensi</button>
                            <button onClick={() => setActiveTab('drive-guru')} className="p-5 bg-purple-50 text-purple-700 rounded-2xl text-sm font-bold hover:bg-purple-100 flex flex-col items-center gap-3 border border-purple-100 transition-transform hover:scale-105"><div className="p-3 bg-white rounded-full shadow-sm"><FileText size={24} /></div>Upload Admin</button>
                            <button onClick={() => window.open('https://erapor-zeta.vercel.app/', '_blank')} className="p-5 bg-orange-50 text-orange-700 rounded-2xl text-sm font-bold hover:bg-orange-100 flex flex-col items-center gap-3 border border-orange-100 transition-transform hover:scale-105"><div className="p-3 bg-white rounded-full shadow-sm"><BarChart3 size={24} /></div>Analisis</button>
                        </div>
                    </div>
                </div>
            )}
        </div>
    );
};

const AbsensiGuru = ({ user, teacherAttendance, setTeacherAttendance, classLogs, setClassLogs, schedules, showToast }) => {
    const [status, setStatus] = useState('idle'); 
    const [location, setLocation] = useState(null);
    const today = new Date().toISOString().split('T')[0];
    const isPresent = (teacherAttendance || []).find(a => a.teacherName === user.name && a.date === today);
    
    const getAddressName = async (latitude, longitude) => {
        try {
            const response = await fetch(`https://nominatim.openstreetmap.org/reverse?format=json&lat=${latitude}&lon=${longitude}&zoom=18&addressdetails=1`);
            const data = await response.json();
            const road = data.address?.road || '';
            const suburb = data.address?.suburb || data.address?.village || '';
            const city = data.address?.city || data.address?.town || '';
            const displayName = `${road} ${suburb}, ${city}`.trim();
            return displayName || data.display_name?.split(',')[0] || "Lokasi GPS Terdeteksi";
        } catch (error) {
            return "Area Sekitar Sekolah (GPS)";
        }
    };

    const handleAbsen = () => {
        setStatus('loading');
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(
                async (position) => {
                    const { latitude, longitude } = position.coords;
                    const locationName = await getAddressName(latitude, longitude); 
                    setLocation({ latitude, longitude, name: locationName });
                    
                    setTimeout(() => {
                        const newRecord = {
                            id: Date.now(),
                            teacherName: user.name,
                            date: today,
                            time: new Date().toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit' }),
                            location: { latitude, longitude, name: locationName },
                            status: 'Hadir'
                        };
                        setTeacherAttendance((prev) => [...(prev || []), newRecord]);
                        setStatus('success');
                        showToast(`Absensi Masuk Berhasil di: ${locationName}`);
                    }, 500);
                },
                (error) => {
                    setStatus('error');
                    showToast("Gagal mendapatkan lokasi. Pastikan GPS aktif.", "error");
                }
            );
        } else {
            showToast("Geolocation tidak didukung browser ini.", "error");
            setStatus('error');
        }
    };

    const todayDate = new Date();
    const days = ['Minggu', 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'];
    const activeDay = days[todayDate.getDay()];
    
    const todaysSchedules = (schedules || []).filter(s => s.day === activeDay && s.teacherName === user.name).sort((a, b) => (a.time || '').localeCompare(b.time || ''));
    
    const handleMasukKelas = (schedule) => {
        const timestamp = new Date().toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit' });
        const newLog = {
            id: Date.now(),
            teacherName: user.name,
            className: schedule.class,
            subject: schedule.subject,
            time: timestamp,
            scheduleId: schedule.id,
            date: today 
        };
        setClassLogs((prev) => [...(prev || []), newLog]);
        showToast(`Berhasil masuk kelas ${schedule.class}`);
    };

    return (
        <div className="space-y-6">
            <div className="flex justify-between items-center bg-white p-6 rounded-2xl border border-slate-100 shadow-sm">
                <div className="flex items-center gap-4">
                    <div className="p-3 bg-teal-100 text-teal-600 rounded-xl"><MapPin size={32} /></div>
                    <div><h2 className="text-2xl font-bold text-slate-800">Absensi Kehadiran</h2><p className="text-slate-500 text-sm">Catat kehadiran harian & masuk kelas</p></div>
                </div>
            </div>
            
            <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div className="bg-white p-8 rounded-2xl shadow-lg border border-slate-100 flex flex-col items-center justify-center text-center">
                    <h3 className="text-xl font-bold text-slate-800 mb-2">Status Kehadiran Hari Ini</h3>
                    <p className="text-slate-500 mb-8">{new Date().toLocaleDateString('id-ID', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}</p>
                    
                    {isPresent ? (
                        <div className="bg-emerald-50 border border-emerald-200 rounded-2xl p-6 w-full animate-fade-in">
                            <div className="w-16 h-16 bg-emerald-100 text-emerald-600 rounded-full flex items-center justify-center mx-auto mb-4"><CheckCircle size={32} /></div>
                            <h4 className="text-lg font-bold text-emerald-800 mb-1">Sudah Absen Masuk</h4>
                            <p className="text-emerald-600 text-sm font-bold">Pukul: {isPresent.time}</p>
                            <p className="text-emerald-600 text-xs mt-2 flex items-center justify-center gap-1">
                                <MapPin size={12} /> {isPresent.location?.name || 'Lokasi Terdeteksi'}
                            </p>
                        </div>
                    ) : (
                        <div className="w-full">
                            {status === 'loading' ? (
                                <div className="py-8 flex flex-col items-center"><div className="animate-spin rounded-full h-12 w-12 border-b-2 border-indigo-600 mb-4"></div><p className="text-indigo-600 font-medium">Mendeteksi Lokasi...</p></div>
                            ) : (
                                <button onClick={handleAbsen} className="w-full py-4 bg-gradient-to-r from-teal-500 to-emerald-500 hover:from-teal-600 hover:to-emerald-600 text-white rounded-xl font-bold shadow-lg shadow-emerald-200 transform hover:-translate-y-1 transition-all flex flex-col items-center gap-2">
                                    <Crosshair size={32} /><span>KLIK UNTUK ABSEN MASUK</span><span className="text-xs font-normal opacity-90">Pastikan Izin Lokasi Aktif</span>
                                </button>
                            )}
                        </div>
                    )}
                </div>
                <div className="bg-slate-50 p-8 rounded-2xl border border-dashed border-slate-300 flex flex-col items-center justify-center text-center">
                    <div className="bg-white p-4 rounded-full shadow-sm mb-4"><Clock size={32} className="text-slate-400" /></div>
                    <h4 className="text-lg font-bold text-slate-700 mb-2">Riwayat Absensi</h4>
                    <div className="w-full mt-4 space-y-3">
                        {(teacherAttendance || []).filter(a => a.teacherName === user.name).slice(-3).reverse().map((log, idx) => (
                            <div key={`att-${log.id}-${idx}`} className="bg-white p-3 rounded-xl border border-slate-200 flex justify-between items-center text-sm">
                                <span className="text-slate-600">{log.date}</span>
                                <span className="font-bold text-emerald-600">{log.time}</span>
                            </div>
                        ))}
                        {(teacherAttendance || []).filter(a => a.teacherName === user.name).length === 0 && <p className="text-slate-400 text-sm">Belum ada data.</p>}
                    </div>
                </div>
            </div>
            <div className="mt-8">
                <div className="flex items-center gap-3 mb-4 px-2">
                    <div className="p-2 bg-blue-100 text-blue-600 rounded-lg"><LogIn size={20} /></div>
                    <h3 className="text-lg font-bold text-slate-800">Absensi Masuk Kelas (Jadwal Hari Ini)</h3>
                </div>
                
                {todaysSchedules.length > 0 ? (
                    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                        {todaysSchedules.map((schedule, idx) => {
                            const isEntered = (classLogs || []).some(log => log.scheduleId === schedule.id && log.date === today);
                            
                            return (
                                <div key={`${schedule.id}-${idx}`} className={`p-5 rounded-xl border transition-all ${isEntered ? 'bg-blue-50 border-blue-200' : 'bg-white border-slate-200 hover:border-blue-400 shadow-sm'}`}>
                                    <div className="flex justify-between items-start mb-2">
                                        <span className="font-bold text-slate-800 text-lg">{schedule.class}</span>
                                        <span className="text-xs font-mono bg-slate-100 px-2 py-1 rounded text-slate-500">{schedule.time || '--:--'}</span>
                                    </div>
                                    <p className="text-slate-600 text-sm mb-4">{schedule.subject} - Ruang {schedule.room}</p>
                                    
                                    {isEntered ? (
                                        <button disabled className="w-full py-2 bg-blue-100 text-blue-700 font-bold rounded-lg text-sm flex items-center justify-center gap-2 cursor-default">
                                            <CheckCircle size={16} /> Sudah Masuk
                                        </button>
                                    ) : (
                                        <button onClick={() => handleMasukKelas(schedule)} className="w-full py-2 bg-blue-600 text-white font-bold rounded-lg text-sm hover:bg-blue-700 transition-colors flex items-center justify-center gap-2 shadow-md shadow-blue-200">
                                            <LogIn size={16} /> Masuk Kelas
                                        </button>
                                    )}
                                </div>
                            );
                        })}
                    </div>
                ) : (
                    <div className="p-12 text-center text-slate-400 bg-slate-50 rounded-xl border border-dashed border-slate-200 flex flex-col items-center">
                        <Calendar size={48} className="text-slate-300 mb-4" />
                        <p className="font-medium">Hari ini tidak ada jadwal mengajar.</p>
                    </div>
                )}
            </div>
        </div>
    );
};

const JadwalGuru = ({ user, schedules }) => {
    const days = ['Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'];
    const mySchedules = (schedules || []).filter(s => s.teacherName === user.name);
    return (
        <div className="space-y-6">
            <div className="flex justify-between items-center bg-white p-6 rounded-2xl border border-slate-100 shadow-sm"><div className="flex items-center gap-4"><div className="p-3 bg-indigo-100 text-indigo-600 rounded-xl"><Calendar size={32} /></div><div><h2 className="text-2xl font-bold text-slate-800">Jadwal Mengajar Saya</h2></div></div></div>
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                {days.map((day, dIdx) => {
                    const daily = mySchedules.filter(s => s.day === day).sort((a,b) => (a.time||'').localeCompare(b.time||''));
                    if (daily.length === 0) return null;
                    return (
                        <div key={dIdx} className="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden"><div className="bg-slate-50 px-6 py-4 border-b border-slate-200"><h3 className="font-bold text-slate-800">{day}</h3></div><div className="divide-y divide-slate-100">{daily.map((sc, idx) => (<div key={idx} className="p-4 hover:bg-slate-50"><div className="flex justify-between mb-1"><span className="font-bold text-indigo-600 font-mono text-sm">Jam {sc.jamKe || '-'} ({sc.time})</span><span className="px-2 py-0.5 bg-slate-100 text-slate-600 rounded text-xs font-bold border border-slate-200">{sc.class}</span></div><h4 className="font-bold text-slate-700">{sc.subject}</h4><div className="flex items-center gap-1 text-xs text-slate-500 mt-1"><MapPin size={12} /> Ruang {sc.room}</div></div>))}</div></div>
                    );
                })}
            </div>
        </div>
    );
};

const JurnalMengajar = ({ user, schedules, students, attendance, setJurnals, jurnals, showToast, schoolConfig, teachers }) => {
    const [selectedDate, setSelectedDate] = useState(new Date());
    const [selectedSchedule, setSelectedSchedule] = useState(null);
    const [form, setForm] = useState({ tujuan: '', kegiatan: '', refleksi: '', catatan: '' });
    const activeDay = ['Minggu', 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'][selectedDate.getDay()];
    const dateStr = selectedDate.toLocaleDateString('id-ID');

    const getAbsentStudents = (className) => {
        const classStudents = (students || []).filter(s => s.class === className);
        const absent = classStudents.filter(s => {
            const status = attendance[s.id];
            return status && status !== 'Hadir';
        });
        if (absent.length === 0) return 'Nihil';
        return absent.map(s => `${s.name} (${attendance[s.id]})`).join(', ');
    };

    const handleDownloadPDF = async () => {
        try {
            const { jsPDF } = await import('https://esm.sh/jspdf@2.5.1');
            const autoTable = (await import('https://esm.sh/jspdf-autotable@3.5.29')).default;
            const doc = new jsPDF('landscape'); // Menggunakan orientasi landscape agar muat banyak kolom
            const myJurnals = (jurnals || []).filter(j => j.teacherName === user.name).sort((a,b) => new Date(a.date) - new Date(b.date));
            const currentTeacher = (teachers || []).find(t => t.name === user.name);

            // --- KOP SURAT ---
            doc.setFontSize(16);
            doc.setFont("helvetica", "bold");
            doc.text(schoolConfig?.name || 'NAMA SEKOLAH BELUM DIATUR', 148, 15, { align: 'center' });
            
            doc.setFontSize(10);
            doc.setFont("helvetica", "normal");
            doc.text(schoolConfig?.address || 'Alamat Sekolah Belum Diatur', 148, 22, { align: 'center' });
            doc.text(`Email: ${schoolConfig?.email || '-'}  |  NPSN: ${schoolConfig?.npsn || '-'}`, 148, 27, { align: 'center' });
            
            // Garis pembatas Kop Surat
            doc.setLineWidth(0.5);
            doc.line(14, 31, 283, 31);
            doc.setLineWidth(0.1);
            doc.line(14, 32, 283, 32);

            // --- IDENTITAS GURU & PELAJARAN ---
            doc.setFontSize(12);
            doc.setFont("helvetica", "bold");
            doc.text('JURNAL MENGAJAR GURU', 148, 42, { align: 'center' });

            doc.setFontSize(10);
            doc.setFont("helvetica", "normal");
            
            doc.text(`Nama Guru`, 14, 52); doc.text(`:  ${user.name}`, 40, 52);
            doc.text(`NIP`, 14, 58); doc.text(`:  ${currentTeacher?.nip || '-'}`, 40, 58);
            doc.text(`Mata Pelajaran`, 14, 64); doc.text(`:  ${currentTeacher?.mapel || '-'}`, 40, 64);
            
            doc.text(`Tahun Pelajaran`, 200, 52); doc.text(`:  ${schoolConfig?.academicYear || '-'}`, 235, 52);
            doc.text(`Semester`, 200, 58); doc.text(`:  ${schoolConfig?.semester || '-'}`, 235, 58);

            // --- TABEL JURNAL ---
            const columns = [
                { header: 'No', dataKey: 'no' },
                { header: 'Hari/Tanggal', dataKey: 'tanggal' },
                { header: 'Jam Ke', dataKey: 'jam' },
                { header: 'Kelas', dataKey: 'kelas' },
                { header: 'Tujuan Pembelajaran', dataKey: 'tujuan' },
                { header: 'Kegiatan Pembelajaran', dataKey: 'kegiatan' },
                { header: 'Refleksi & Catatan', dataKey: 'refleksi' },
                { header: 'Siswa Absen', dataKey: 'absen' },
            ];

            const body = myJurnals.map((j, index) => ({
                no: index + 1,
                tanggal: `${j.day},\n${j.date}`,
                jam: `${j.jamKe || '-'}\n(${j.time})`,
                kelas: j.class,
                tujuan: j.tujuan,
                kegiatan: j.kegiatan,
                refleksi: `Refleksi:\n${j.refleksi}\n\nCatatan:\n${j.catatan}`,
                absen: j.absentStudents || 'Nihil'
            }));

            autoTable(doc, {
                columns: columns,
                body: body,
                startY: 70,
                styles: { fontSize: 9, cellPadding: 3, valign: 'middle' },
                headStyles: { fillColor: [79, 70, 229], textColor: 255, halign: 'center' },
                columnStyles: {
                    no: { halign: 'center', cellWidth: 10 },
                    tanggal: { cellWidth: 25 },
                    jam: { cellWidth: 25, halign: 'center' },
                    kelas: { halign: 'center', cellWidth: 15 },
                    tujuan: { cellWidth: 'auto' },
                    kegiatan: { cellWidth: 'auto' },
                    refleksi: { cellWidth: 'auto' },
                    absen: { cellWidth: 30 }
                },
                theme: 'grid',
            });

            // --- TANDA TANGAN ---
            const finalY = doc.lastAutoTable.finalY + 15;
            if (finalY < 170) {
                // Cari data Kepala Sekolah dari array teachers
                const principal = (teachers || []).find(t => t.status && t.status.toLowerCase().includes('kepala sekolah'));
                const principalName = principal ? principal.name : '.......................................................';
                const principalNip = principal && principal.nip && principal.nip !== '-' ? `NIP. ${principal.nip}` : '';

                // Bagian Kepala Sekolah (Kiri) - Rata Tengah di koordinat x=55
                doc.text(`Mengetahui,`, 55, finalY, { align: 'center' });
                doc.text(`Kepala Sekolah`, 55, finalY + 5, { align: 'center' });
                
                doc.setFont("helvetica", "bold");
                doc.text(`${principalName}`, 55, finalY + 25, { align: 'center' });
                doc.setFont("helvetica", "normal");
                
                if (principalNip) {
                    doc.text(principalNip, 55, finalY + 30, { align: 'center' });
                }

                // Bagian Guru (Kanan) - Rata Tengah di koordinat x=235
                // Ambil nama kota dari alamat (kata terakhir setelah koma), atau gunakan titik-titik jika tidak ada
                const city = schoolConfig?.address ? schoolConfig.address.split(',').pop().trim() : '...................';
                
                doc.text(`${city}, ${new Date().toLocaleDateString('id-ID', { day: 'numeric', month: 'long', year: 'numeric' })}`, 235, finalY, { align: 'center' });
                doc.text(`Guru Mata Pelajaran`, 235, finalY + 5, { align: 'center' });
                
                doc.setFont("helvetica", "bold");
                doc.text(`${user.name}`, 235, finalY + 25, { align: 'center' });
                doc.setFont("helvetica", "normal");
                
                if(currentTeacher?.nip && currentTeacher.nip !== '-') {
                    doc.text(`NIP. ${currentTeacher.nip}`, 235, finalY + 30, { align: 'center' });
                }
            }

            doc.save(`Jurnal_Mengajar_${user.name.replace(/\s/g, '_')}.pdf`);
            showToast("Laporan Jurnal Mengajar berhasil diunduh!", "success");
        } catch(e) {
            console.error(e);
            showToast("Gagal membuat laporan PDF. Pastikan koneksi internet stabil.", "error");
        }
    };

    const isFormValid = useMemo(() => {
        return form.tujuan.trim() !== '' && form.kegiatan.trim() !== '' && form.refleksi.trim() !== '' && form.catatan.trim() !== '';
    }, [form]);

    return (
        <div className="space-y-6">
            <div className="flex flex-col md:flex-row justify-between items-center gap-4 bg-white p-6 rounded-2xl border border-slate-100 shadow-sm"><div className="flex items-center gap-4"><div className="p-3 bg-blue-100 text-blue-600 rounded-xl"><Book size={32} /></div><div><h2 className="text-2xl font-bold text-slate-800">Jurnal Mengajar</h2><p className="text-slate-500 text-sm">Catatan harian kegiatan pembelajaran di kelas</p></div></div><div className="flex items-center gap-3 bg-slate-50 p-2 rounded-xl border border-slate-200 w-full md:w-auto"><input type="date" value={selectedDate.toISOString().split('T')[0]} onChange={(e) => { setSelectedDate(new Date(e.target.value)); setSelectedSchedule(null); }} className="bg-white border rounded-lg focus:ring-blue-500 p-2.5 outline-none font-bold" /><button onClick={handleDownloadPDF} className="bg-red-500 hover:bg-red-600 text-white p-2.5 rounded-lg flex items-center gap-2 font-bold transition-colors"><Download size={18} /> PDF</button></div></div>
            {!selectedSchedule ? (
                <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                    {(schedules || []).filter(s => s.day === activeDay).map(item => {
                        const existingJournal = (jurnals || []).find(j => j.scheduleId === item.id && j.date === dateStr);
                        const isFilled = !!existingJournal;
                        return (
                            <div key={item.id} onClick={() => { 
                                setSelectedSchedule(item); 
                                if(isFilled) { setForm({ tujuan: existingJournal.tujuan, kegiatan: existingJournal.kegiatan, refleksi: existingJournal.refleksi, catatan: existingJournal.catatan }); showToast("Memuat jurnal untuk diedit."); }
                                else { setForm({tujuan:'', kegiatan:'', refleksi:'', catatan:''}); }
                            }} className={`bg-white p-6 rounded-xl border cursor-pointer hover:shadow-md transition-all ${isFilled ? 'border-emerald-200 bg-emerald-50/30' : 'border-slate-200'}`}>
                                <div className="flex justify-between items-start mb-2"><span className={`px-3 py-1 text-xs font-bold rounded-lg ${isFilled?'bg-emerald-100 text-emerald-700':'bg-slate-100 text-slate-600'}`}>Jam {item.jamKe || '-'} ({item.time})</span><span className={`text-xs ${isFilled?'text-emerald-600 font-bold':'text-slate-400'}`}>{isFilled?'Sudah Diisi (Klik untuk Edit)':'Klik untuk isi'}</span></div>
                                <h4 className="font-bold text-lg text-slate-800">{item.subject}</h4><p className="text-slate-500 text-sm">Kelas {item.class} • Ruang {item.room}</p>
                            </div>
                        )
                    })}
                    {(schedules || []).filter(s => s.day === activeDay).length === 0 && (
                        <div className="col-span-full p-12 text-center text-slate-400 bg-slate-50 rounded-xl border border-dashed border-slate-200">
                            Anda tidak memiliki jadwal mengajar pada hari ini. Form jurnal tidak tersedia.
                        </div>
                    )}
                </div>
            ) : (
                <div className="bg-white p-8 rounded-2xl border border-slate-200 shadow-sm animate-fade-in-down">
                    <div className="flex justify-between items-center mb-6 border-b border-slate-100 pb-4"><h3 className="font-bold text-xl text-slate-800">Isi Jurnal Kelas {selectedSchedule.class}</h3><button onClick={() => setSelectedSchedule(null)} className="text-slate-400 hover:text-slate-600"><X size={24} /></button></div>
                    <div className="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                        <div><label className="block text-xs font-bold text-slate-500 uppercase tracking-wider mb-2">Siswa Tidak Hadir</label><div className="p-3 bg-red-50 text-red-700 font-medium border border-red-100 rounded-xl">{getAbsentStudents(selectedSchedule.class)}</div><p className="text-[10px] text-slate-400 mt-1">*Data diambil dari menu Presensi</p></div>
                    </div>
                    <div className="space-y-4">
                        <div><label className="block text-sm font-bold text-slate-700 mb-2">Tujuan Pembelajaran</label><textarea className="w-full p-4 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" rows="2" value={form.tujuan} onChange={e => setForm({...form, tujuan: e.target.value})}></textarea></div>
                        <div><label className="block text-sm font-bold text-slate-700 mb-2">Kegiatan Pembelajaran / ATP</label><textarea className="w-full p-4 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" rows="3" value={form.kegiatan} onChange={e => setForm({...form, kegiatan: e.target.value})}></textarea></div>
                        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div><label className="block text-sm font-bold text-slate-700 mb-2">Refleksi Guru</label><textarea className="w-full p-4 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" rows="2" value={form.refleksi} onChange={e => setForm({...form, refleksi: e.target.value})}></textarea></div>
                            <div><label className="block text-sm font-bold text-slate-700 mb-2">Catatan Kejadian</label><textarea className="w-full p-4 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" rows="2" value={form.catatan} onChange={e => setForm({...form, catatan: e.target.value})}></textarea></div>
                        </div>
                    </div>
                    <div className="mt-8 flex justify-end gap-3"><button onClick={() => setSelectedSchedule(null)} className="px-6 py-3 bg-slate-100 text-slate-600 font-bold rounded-xl hover:bg-slate-200">Batal</button>
                    <button disabled={!isFormValid} onClick={() => { 
                        setJurnals(p => {
                            const updated = [...(p || [])];
                            const idx = updated.findIndex(j => j.scheduleId === selectedSchedule.id && j.date === dateStr);
                            const journalData = { ...selectedSchedule, ...form, date: dateStr, teacherName: user.name, absentStudents: getAbsentStudents(selectedSchedule.class) };
                            if(idx > -1) { updated[idx] = { ...updated[idx], ...journalData }; } 
                            else { updated.push({ ...journalData, id: Date.now() }); }
                            return updated;
                        }); 
                        showToast('Jurnal Berhasil Disimpan', 'success'); 
                        setSelectedSchedule(null); 
                    }} className={`px-6 py-3 font-bold rounded-xl flex items-center gap-2 transition-all ${isFormValid ? 'bg-blue-600 text-white hover:bg-blue-700 shadow-md' : 'bg-slate-300 text-slate-500 cursor-not-allowed'}`}><Save size={18}/> Simpan Jurnal</button></div>
                </div>
            )}
        </div>
    );
};

const DriveAdministrasiGuru = ({ teacherDriveLinks, setTeacherDriveLinks, user, showToast }) => {
    const handleFolder = (id) => {
        const link = (teacherDriveLinks || {})[user.id]?.[id];
        link ? window.open(link, '_blank') : showToast('Link belum diset Admin.', 'error');
    };
    return (
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            {[{id:'perangkat', title:'Perangkat Ajar', col:'bg-blue-100 text-blue-600'}, {id:'sas_sat', title:'Administrasi SAS/SAT', col:'bg-emerald-100 text-emerald-600'}, {id:'psaj', title:'Administrasi PSAJ', col:'bg-orange-100 text-orange-600'}].map(f => (
                <button key={f.id} onClick={() => handleFolder(f.id)} className="bg-white p-6 rounded-2xl border shadow-sm hover:shadow-lg flex flex-col items-center justify-center h-48 group transition-all">
                    <div className={`p-4 rounded-full mb-4 group-hover:scale-110 transition-transform ${f.col}`}><Folder size={48} /></div><h3 className="font-bold text-slate-800">{f.title}</h3>
                </button>
            ))}
        </div>
    );
};

const PresensiSiswa = ({ students, attendance, setAttendance, showToast, user, schedules, classes }) => {
    const today = new Date();
    const activeDay = ['Minggu', 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'][today.getDay()];
    
    // Penyaringan kelas berdasarkan jadwal guru hari ini
    const availableClasses = useMemo(() => {
        if (user.role === 'admin' || user.role === 'kepala_sekolah') {
            return (classes || []).map(c => c.name);
        } else {
            const todaysSchedules = (schedules || []).filter(s => s.day === activeDay && s.teacherName === user.name);
            return [...new Set(todaysSchedules.map(s => s.class))];
        }
    }, [user, schedules, activeDay, classes]);

    const [selectedClass, setSelectedClass] = useState('');

    useEffect(() => {
        if (availableClasses.length > 0 && !availableClasses.includes(selectedClass)) {
            setSelectedClass(availableClasses[0]);
        }
    }, [availableClasses, selectedClass]);

    return (
        <div className="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden">
            <div className="p-6 border-b flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
                <div>
                    <h2 className="text-xl font-bold">Presensi Siswa</h2>
                    <p className="text-sm text-slate-500">Pilih kelas berdasarkan jadwal Anda hari ini</p>
                </div>
                <div className="flex gap-3 w-full md:w-auto">
                    <select value={selectedClass} onChange={e => setSelectedClass(e.target.value)} className="p-2.5 border border-slate-300 rounded-xl flex-1 bg-slate-50 font-bold focus:outline-none focus:ring-2 focus:ring-emerald-500">
                        {availableClasses.length > 0 ? availableClasses.map(c => <option key={c} value={c}>Kelas {c}</option>) : <option value="">Tidak ada jadwal hari ini</option>}
                    </select>
                    <button onClick={() => showToast('Data Presensi Disimpan', 'success')} className="bg-emerald-600 hover:bg-emerald-700 text-white px-5 py-2.5 rounded-xl font-bold flex items-center gap-2 transition-all shadow-md"><Save size={18}/> Simpan</button>
                </div>
            </div>
            <div className="overflow-x-auto">
                {availableClasses.length > 0 ? (
                    <table className="w-full text-left text-sm min-w-[600px]">
                        <thead className="bg-slate-50 border-b"><tr><th className="p-4 text-slate-700">Nama Siswa</th><th className="p-4 text-slate-700">Status</th></tr></thead>
                        <tbody className="divide-y">{(students || []).filter(s => s.class === selectedClass).map(s => (
                            <tr key={s.id} className="hover:bg-slate-50"><td className="p-4 font-bold text-slate-800">{s.name} <span className="block text-xs font-normal text-slate-500">{s.class}</span></td><td className="p-4"><div className="flex gap-2">{['Hadir', 'Sakit', 'Izin', 'Alpha'].map(status => (
                                <button key={status} onClick={() => setAttendance(p => ({...(p || {}), [s.id]: status}))} className={`px-4 py-1.5 rounded-lg text-xs font-bold border transition-all ${((attendance || {})[s.id] || 'Hadir') === status ? 'bg-emerald-100 text-emerald-700 border-emerald-400 shadow-sm' : 'bg-white text-slate-500 hover:bg-slate-50'}`}>{status}</button>
                            ))}</div></td></tr>
                        ))}
                        {(students || []).filter(s => s.class === selectedClass).length === 0 && (
                            <tr><td colSpan="2" className="p-8 text-center text-slate-400">Belum ada data siswa di kelas ini.</td></tr>
                        )}
                        </tbody>
                    </table>
                ) : (
                    <div className="p-12 text-center text-slate-400">Anda tidak memiliki jadwal mengajar hari ini. Presensi tidak dapat diisi.</div>
                )}
            </div>
        </div>
    );
};

const MonitoringGuru = ({ teacherAttendance, classLogs, schedules, jurnals, teachers }) => {
    const today = new Date();
    const days = ['Minggu', 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'];
    const activeDay = days[today.getDay()];
    const todayLocale = today.toLocaleDateString('id-ID');
    
    const teacherStatus = useMemo(() => {
        const todaysSchedules = (schedules || []).filter(s => s.day === activeDay);
        const activeTeachers = [...new Set(todaysSchedules.map(s => s.teacherName))];
        return activeTeachers.map(teacherName => {
            const teacherSchedules = todaysSchedules.filter(s => s.teacherName === teacherName);
            const filledCount = teacherSchedules.reduce((acc, sch) => {
                 const hasFilled = (jurnals || []).some(j => j.scheduleId === sch.id && j.date === todayLocale);
                 return acc + (hasFilled ? 1 : 0);
            }, 0);
            return {
                name: teacherName,
                totalClasses: teacherSchedules.length,
                filledClasses: filledCount,
                progress: Math.round((filledCount / teacherSchedules.length) * 100)
            };
        }).sort((a, b) => b.progress - a.progress); 
    }, [schedules, jurnals, activeDay, todayLocale]);

    return (
        <div className="space-y-8 animate-fade-in">
            <div className="flex justify-between items-center bg-white p-6 rounded-2xl border border-slate-100 shadow-sm"><div className="flex items-center gap-4"><div className="p-3 bg-purple-100 text-purple-600 rounded-xl"><Activity size={32} /></div><div><h2 className="text-2xl font-bold text-slate-800">Monitoring Guru</h2><p className="text-slate-500 text-sm">Pantau kehadiran guru, aktivitas kelas, dan pengisian jurnal secara real-time</p></div></div></div>
            <div className="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden">
                <div className="p-6 border-b border-slate-100 bg-orange-50/50 flex justify-between items-center"><h3 className="font-bold text-lg text-orange-800 flex items-center gap-2"><Book size={20} /> Progres Pengisian Jurnal Hari Ini</h3><span className="bg-white px-3 py-1 rounded-lg text-xs font-bold text-orange-600 border border-orange-100">{activeDay}, {todayLocale}</span></div>
                <div className="p-0 overflow-x-auto">
                    {teacherStatus.length > 0 ? (
                        <table className="w-full text-left text-sm min-w-[600px]">
                            <thead className="bg-slate-50"><tr><th className="px-6 py-3 font-semibold text-slate-600">Nama Guru</th><th className="px-6 py-3 font-semibold text-slate-600 text-center">Jadwal Hari Ini</th><th className="px-6 py-3 font-semibold text-slate-600 text-center">Jurnal Terisi</th><th className="px-6 py-3 font-semibold text-slate-600">Status</th></tr></thead>
                            <tbody className="divide-y divide-slate-100">
                                {teacherStatus.map((stat, idx) => (
                                    <tr key={idx} className="hover:bg-slate-50"><td className="px-6 py-4 font-bold text-slate-800">{stat.name}</td><td className="px-6 py-4 text-center"><span className="bg-slate-100 px-2 py-1 rounded font-bold text-slate-600">{stat.totalClasses} Kelas</span></td><td className="px-6 py-4 text-center"><span className={`px-2 py-1 rounded font-bold ${stat.filledClasses === stat.totalClasses ? 'bg-emerald-100 text-emerald-700' : 'bg-yellow-100 text-yellow-700'}`}>{stat.filledClasses}</span></td><td className="px-6 py-4"><div className="w-full bg-slate-200 rounded-full h-2.5 w-32"><div className={`h-2.5 rounded-full ${stat.progress === 100 ? 'bg-emerald-500' : 'bg-indigo-500'}`} style={{ width: `${stat.progress}%` }}></div></div><span className="text-xs text-slate-500 mt-1 block">{stat.progress}% Selesai</span></td></tr>
                                ))}
                            </tbody>
                        </table>
                    ) : (<div className="p-8 text-center text-slate-400">Tidak ada jadwal mengajar hari ini.</div>)}
                </div>
            </div>
            <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div className="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden">
                    <div className="p-6 border-b border-slate-100 bg-purple-50/50 flex justify-between items-center"><h3 className="font-bold text-lg text-purple-800 flex items-center gap-2"><MapPin size={20} /> Kehadiran (GPS)</h3><span className="bg-white px-3 py-1 rounded-lg text-xs font-bold text-purple-600 border border-purple-100">Hari Ini</span></div>
                    <div className="p-0 overflow-x-auto">
                        <table className="w-full text-left text-sm"><thead className="bg-slate-50"><tr><th className="px-6 py-3 font-semibold text-slate-600">Guru</th><th className="px-6 py-3 font-semibold text-slate-600">Waktu</th><th className="px-6 py-3 font-semibold text-slate-600 text-right">Status</th></tr></thead><tbody className="divide-y divide-slate-100">
                            {(teachers || []).map(t => {
                                const log = (teacherAttendance || []).find(a => a.teacherName === t.name && a.date === today.toISOString().split('T')[0]);
                                return (<tr key={t.id} className="hover:bg-slate-50"><td className="px-6 py-4 font-bold text-slate-800">{t.name}</td><td className="px-6 py-4 text-slate-500">{log ? log.time : '-'}</td><td className="px-6 py-4 text-right">{log ? <span className="inline-flex items-center gap-1 px-2.5 py-1 bg-emerald-100 text-emerald-700 rounded-full text-xs font-bold"><CheckCircle size={12} /> Hadir</span> : <span className="text-slate-400 text-xs font-bold">Belum Absen</span>}</td></tr>);
                            })}
                        </tbody></table>
                    </div>
                </div>
                <div className="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden">
                    <div className="p-6 border-b border-slate-100 bg-blue-50/50 flex justify-between items-center"><h3 className="font-bold text-lg text-blue-800 flex items-center gap-2"><LogIn size={20} /> Aktivitas Masuk Kelas</h3><span className="bg-white px-3 py-1 rounded-lg text-xs font-bold text-blue-600 border border-blue-100">Real-time</span></div>
                    <div className="p-0 overflow-x-auto">
                        {(classLogs || []).length > 0 ? (
                            <table className="w-full text-left text-sm"><thead className="bg-slate-50"><tr><th className="px-6 py-3 font-semibold text-slate-600">Guru</th><th className="px-6 py-3 font-semibold text-slate-600">Kelas / Mapel</th><th className="px-6 py-3 font-semibold text-slate-600 text-right">Jam Masuk</th></tr></thead><tbody className="divide-y divide-slate-100">
                                {(classLogs || []).slice(0, 10).map((log, idx) => (<tr key={idx} className="hover:bg-slate-50"><td className="px-6 py-4 font-bold text-slate-800">{log.teacherName}</td><td className="px-6 py-4"><div className="text-slate-800 font-bold">{log.className}</div><div className="text-xs text-slate-500">{log.subject}</div></td><td className="px-6 py-4 text-right text-blue-600 font-mono font-medium">{log.time}</td></tr>))}
                            </tbody></table>
                        ) : (<div className="p-8 text-center text-slate-400">Belum ada aktivitas masuk kelas hari ini.</div>)}
                    </div>
                </div>
            </div>
        </div>
    );
};

const AnalisisSiswa = ({ classes, students, attendance, jurnals, user, isWaliKelas, managedClass, isManagement }) => {
    const [selectedClass, setSelectedClass] = useState('');
    useEffect(() => {
        if (isWaliKelas && managedClass) setSelectedClass(managedClass);
        else if ((isManagement || user?.role === 'admin') && (classes || []).length > 0 && !selectedClass) setSelectedClass((classes || [])[0]?.name);
    }, [classes, isWaliKelas, managedClass, isManagement, user, selectedClass]);

    const analysisData = useMemo(() => {
        if (!selectedClass) return null;
        const classStudents = (students || []).filter(s => s.class === selectedClass);
        const totalStudents = classStudents.length;
        if (totalStudents === 0) return { error: "Belum ada data siswa di kelas ini." };
        const relevantJournals = (jurnals || []).filter(j => j.class === selectedClass);
        
        const absenceFrequency = {};
        let totalPossiblePresent = 0;
        let totalActualPresent = 0;
        relevantJournals.forEach(j => {
            totalPossiblePresent += totalStudents;
            const absents = j.absentStudents && j.absentStudents !== 'Nihil' ? j.absentStudents.split(', ') : [];
            totalActualPresent += (totalStudents - absents.length);
            absents.forEach(entry => {
                const name = entry.split('(')[0].trim();
                if (name) absenceFrequency[name] = (absenceFrequency[name] || 0) + 1;
            });
        });
        const attendanceRate = totalPossiblePresent > 0 ? Math.round((totalActualPresent / totalPossiblePresent) * 100) : 100;
        const atRiskStudents = Object.entries(absenceFrequency).filter(([_, count]) => count > 2).sort((a, b) => b[1] - a[1]).map(([name, count]) => ({ name, count }));
        const teacherNotes = relevantJournals.filter(j => j.catatan && j.catatan.length > 5).map(j => ({ date: j.date, subject: j.subject, teacher: j.teacherName, note: j.catatan })).sort((a, b) => new Date(b.date) - new Date(a.date)); 
        
        let description = `Kelas **${selectedClass}** memiliki total **${totalStudents} siswa**. Berdasarkan data jurnal dari seluruh guru, tingkat kehadiran rata-rata kelas ini adalah **${attendanceRate}%**. `;
        if (attendanceRate >= 90) description += "Kedisiplinan kehadiran kelas ini tergolong **sangat baik**. ";
        else if (attendanceRate >= 75) description += "Kehadiran cukup baik, namun perlu ditingkatkan. ";
        else description += "Perlu **intervensi khusus** karena tingkat ketidakhadiran yang tinggi. ";
        if (atRiskStudents.length > 0) description += `Siswa yang paling sering absen adalah: **${atRiskStudents.slice(0, 3).map(s => s.name).join(", ")}**. Mohon perhatian khusus dari Wali Kelas dan BK. `;
        else description += "Tidak ada siswa dengan absensi berulang yang signifikan. ";
        if (teacherNotes.length > 0) description += `Tercatat **${teacherNotes.length} catatan perilaku/kejadian** dari guru. Catatan terbaru dari ${teacherNotes[0].teacher} menyebutkan: "${teacherNotes[0].note}".`;
        else description += "Belum ada catatan kejadian khusus yang dilaporkan guru mata pelajaran.";
        
        return { totalStudents, attendanceRate, atRiskStudents, teacherNotes, description, journalCount: relevantJournals.length };
    }, [selectedClass, students, jurnals]);

    return (
        <div className="space-y-8 animate-fade-in">
            <div className="flex flex-col md:flex-row justify-between items-center gap-4 bg-white p-6 rounded-2xl border border-slate-100 shadow-sm">
                <div className="flex items-center gap-4">
                    <div className="p-3 bg-purple-100 text-purple-600 rounded-xl"><BrainCircuit size={32} /></div>
                    <div><h2 className="text-2xl font-bold text-slate-800">Analisis Siswa & Kelas</h2><p className="text-slate-500 text-sm">Insight otomatis berbasis data jurnal dan kehadiran</p></div>
                </div>
                <div className="relative min-w-[200px]">
                    {isWaliKelas ? (
                        <div className="bg-slate-100 px-4 py-3 rounded-xl font-bold text-slate-700 text-center border border-slate-200">Kelas {selectedClass}</div>
                    ) : (
                        <select value={selectedClass} onChange={(e) => setSelectedClass(e.target.value)} className="w-full bg-slate-50 border border-slate-200 text-slate-700 py-3 px-4 pr-8 rounded-xl focus:outline-none focus:ring-2 focus:ring-purple-500 font-bold cursor-pointer outline-none">
                            <option value="" disabled>Pilih Kelas</option>
                            {(classes || []).map((c, index) => <option key={index} value={c.name}>{c.name}</option>)}
                        </select>
                    )}
                </div>
            </div>
            {analysisData && !analysisData.error ? (
                <>
                    <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <div className="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm">
                            <p className="text-sm font-bold text-slate-400 uppercase tracking-wider">Rata-rata Kehadiran</p>
                            <div className="flex items-end gap-2 mt-2"><h3 className={`text-4xl font-bold ${analysisData.attendanceRate >= 90 ? 'text-emerald-500' : analysisData.attendanceRate >= 75 ? 'text-yellow-500' : 'text-red-500'}`}>{analysisData.attendanceRate}%</h3><span className="text-sm text-slate-400 mb-1">dari {analysisData.journalCount} pertemuan</span></div>
                            <div className="w-full bg-slate-100 rounded-full h-2 mt-4"><div className={`h-2 rounded-full ${analysisData.attendanceRate >= 90 ? 'bg-emerald-500' : analysisData.attendanceRate >= 75 ? 'bg-yellow-500' : 'bg-red-500'}`} style={{ width: `${analysisData.attendanceRate}%` }}></div></div>
                        </div>
                        <div className="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm">
                            <p className="text-sm font-bold text-slate-400 uppercase tracking-wider">Siswa Perlu Perhatian</p>
                            <h3 className="text-4xl font-bold text-slate-800 mt-2">{analysisData.atRiskStudents.length} <span className="text-lg font-medium text-slate-400">Siswa</span></h3>
                            <p className="text-xs text-slate-500 mt-2">Sering absen ({'>'} 2x) di jurnal.</p>
                        </div>
                        <div className="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm">
                            <p className="text-sm font-bold text-slate-400 uppercase tracking-wider">Total Catatan Guru</p>
                            <h3 className="text-4xl font-bold text-indigo-600 mt-2">{analysisData.teacherNotes.length}</h3>
                            <p className="text-xs text-slate-500 mt-2">Input jurnal kejadian di kelas ini.</p>
                        </div>
                    </div>
                    <div className="bg-gradient-to-br from-indigo-500 to-purple-600 rounded-2xl shadow-lg p-8 text-white relative overflow-hidden">
                        <div className="absolute top-0 right-0 p-4 opacity-10"><BrainCircuit size={120} /></div>
                        <h3 className="text-lg font-bold mb-4 flex items-center gap-2 relative z-10"><span className="bg-white/20 p-1.5 rounded-lg"><Activity size={18} /></span> Analisis Otomatis Kelas {selectedClass}</h3>
                        <p className="text-indigo-50 leading-relaxed text-lg relative z-10 font-light">
                            {analysisData.description.split('. ').map((sentence, i) => <span key={`desc-${i}`} dangerouslySetInnerHTML={{ __html: sentence + (sentence.endsWith('.') ? '' : '. ') }} />)}
                        </p>
                    </div>
                    <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
                        <div className="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden">
                            <div className="p-6 border-b border-slate-100 bg-red-50/50"><h4 className="font-bold text-slate-800 flex items-center gap-2"><AlertCircle size={18} className="text-red-500" /> Siswa dengan Absensi Tertinggi</h4></div>
                            <div className="p-0">
                                {analysisData.atRiskStudents.length > 0 ? (
                                    <table className="w-full text-left text-sm"><thead className="bg-slate-50"><tr><th className="px-6 py-3 font-semibold text-slate-600">Nama Siswa</th><th className="px-6 py-3 font-semibold text-slate-600 text-right">Jml. Absen</th></tr></thead><tbody className="divide-y divide-slate-100">
                                        {analysisData.atRiskStudents.slice(0, 5).map((s, idx) => (<tr key={`risk-${idx}`} className="hover:bg-slate-50"><td className="px-6 py-3 font-medium text-slate-800">{s.name}</td><td className="px-6 py-3 text-right font-bold text-red-600">{s.count}x</td></tr>))}
                                    </tbody></table>
                                ) : (<div className="p-8 text-center text-slate-400">Tidak ada siswa yang berisiko tinggi.</div>)}
                            </div>
                        </div>
                        <div className="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden flex flex-col h-[400px]">
                            <div className="p-6 border-b border-slate-100 bg-blue-50/50 shrink-0"><h4 className="font-bold text-slate-800 flex items-center gap-2"><FileText size={18} className="text-blue-500" /> Catatan Kejadian Guru</h4></div>
                            <div className="p-6 overflow-y-auto flex-1 no-scrollbar space-y-6">
                                {analysisData.teacherNotes.length > 0 ? (
                                    analysisData.teacherNotes.map((note, idx) => (
                                        <div key={`note-${idx}`} className="relative pl-6 border-l-2 border-slate-200 last:border-0 pb-1">
                                            <div className="absolute -left-[9px] top-0 w-4 h-4 rounded-full bg-white border-2 border-indigo-400"></div>
                                            <div className="mb-1 flex justify-between items-start"><span className="text-xs font-bold text-indigo-600 bg-indigo-50 px-2 py-0.5 rounded">{note.subject}</span><span className="text-[10px] text-slate-400">{note.date}</span></div>
                                            <p className="text-sm text-slate-700 italic">"{note.note}"</p>
                                            <p className="text-xs text-slate-400 mt-1 font-medium">- {note.teacher}</p>
                                        </div>
                                    ))
                                ) : (<div className="text-center text-slate-400 mt-12">Belum ada catatan dari guru.</div>)}
                            </div>
                        </div>
                    </div>
                </>
            ) : (<div className="p-12 text-center text-slate-400 bg-slate-50 rounded-xl border border-dashed border-slate-200">Silakan pilih kelas untuk melihat analisis.</div>)}
        </div>
    );
};

const GenerateAkun = ({ teachers, accounts, setAccounts, showToast }) => {
    const handleGenerate = (t) => {
        const uname = t.name.toLowerCase().replace(/[^a-z0-9]/g, '');
        if ((accounts || []).some(a => a.username === uname)) return showToast('Username sudah ada', 'error');
        setAccounts(p => [...(p || []), { username: uname, password: '123', role: 'guru', name: t.name, teacherId: t.id }]);
        showToast(`Akun ${t.name} berhasil dibuat! Password default: 123`, 'success');
    };
    return (
        <div className="bg-white rounded-2xl border border-slate-200 shadow-sm p-6 animate-fade-in"><div className="flex items-center gap-3 mb-6"><div className="p-3 bg-emerald-100 text-emerald-600 rounded-xl"><Key size={24} /></div><div><h2 className="text-xl font-bold text-slate-800">Generate Akun Guru</h2><p className="text-slate-500 text-sm">Klik generate untuk membuat akses login secara otomatis</p></div></div>
            <div className="overflow-x-auto border border-slate-100 rounded-xl">
                <table className="w-full text-left text-sm min-w-[600px]"><thead className="bg-slate-50 border-b"><tr><th className="p-4 text-slate-700 font-bold">Nama Guru</th><th className="p-4 text-slate-700 font-bold">Status Akun</th><th className="p-4 text-slate-700 font-bold">Kredensial</th><th className="p-4 text-right text-slate-700 font-bold">Aksi</th></tr></thead><tbody className="divide-y">{(teachers || []).map(t => {
                    const acc = (accounts || []).find(a => a.name === t.name);
                    return (<tr key={t.id} className="hover:bg-slate-50"><td className="p-4 font-bold text-slate-800">{t.name}</td><td className="p-4">{acc ? <span className="px-2.5 py-1 bg-emerald-100 text-emerald-700 rounded-full text-xs font-bold border border-emerald-200 flex items-center gap-1 w-fit"><CheckCircle size={12} /> Aktif</span> : <span className="px-2.5 py-1 bg-slate-100 text-slate-500 rounded-full text-xs font-bold border border-slate-200">Belum Ada</span>}</td><td className="p-4">{acc ? <div className="font-mono text-xs"><span className="text-indigo-600 font-bold">{acc.username}</span><span className="text-slate-400 mx-2">|</span><span>******</span></div> : <span className="text-slate-400 italic">-</span>}</td><td className="p-4 text-right">{!acc ? <button onClick={() => handleGenerate(t)} className="bg-indigo-600 text-white px-4 py-2 rounded-xl text-xs font-bold shadow-md shadow-indigo-200 hover:bg-indigo-700 transition-all flex items-center justify-end ml-auto gap-2"><Plus size={14}/> Generate</button> : <span className="text-slate-400 text-xs font-bold px-4 py-2">Selesai</span>}</td></tr>)
                })}</tbody></table>
            </div>
        </div>
    )
};

const ManajemenData = ({ teachers, setTeachers, students, setStudents, classes, setClasses, subjects, setSubjects, schedules, setSchedules, showConfirm, showToast, teacherDriveLinks, setTeacherDriveLinks, schoolConfig, setSchoolConfig, schoolDocs, setSchoolDocs, jurnals, setJurnals, teacherAttendance, setTeacherAttendance, classLogs, setClassLogs, accounts, setAccounts, attendance, setAttendance }) => {
    const [tab, setTab] = useState('siswa');
    const [selectedIds, setSelectedIds] = useState([]);
    const [localSchoolConfig, setLocalSchoolConfig] = useState(schoolConfig || INITIAL_SCHOOL_CONFIG);
    
    // --- STATE UNTUK MODAL EDIT ---
    const [showEditModal, setShowEditModal] = useState(false);
    const [editingItem, setEditingItem] = useState(null);
    const [formData, setFormData] = useState({});

    useEffect(() => { 
        setSelectedIds([]); 
    }, [tab]);

    useEffect(() => {
        if (schoolConfig) setLocalSchoolConfig(schoolConfig);
    }, [schoolConfig]);

    const handleDownloadTemplate = async (type) => {
        try {
            const XLSX = await import('https://esm.sh/xlsx@0.18.5');
            let templateData = [];
            if (type === 'siswa') templateData = [{ "Nama Lengkap": "John Doe", "NIS": "2024001", "L/P": "L", "Kelas": "X-A", "Status": "Aktif" }];
            else if (type === 'guru') templateData = [{ "Nama Guru": "Bpk. Budi", "NIP": "19800101", "Mapel": "Matematika", "Tugas Tambahan": "Wali Kelas" }]; 
            else if (type === 'kelas') templateData = [{ "Nama Kelas": "X-A", "Wali Kelas": "Bpk. Budi" }];
            else if (type === 'mapel') templateData = [{ "Kode": "MTK-01", "Nama Mapel": "Matematika", "KKTP": "75" }]; 
            else if (type === 'jadwal') templateData = [{ "Hari": "Senin", "Jam Ke": "1-2", "Kelas": "X-A", "Mapel": "Matematika", "Guru": "Bpk. Budi", "Ruang": "R.101" }];
            
            const ws = XLSX.utils.json_to_sheet(templateData);
            const wb = XLSX.utils.book_new();
            XLSX.utils.book_append_sheet(wb, ws, "Template");
            XLSX.writeFile(wb, `Template_Import_${type}.xlsx`);
            showToast(`Template ${type} berhasil diunduh.`, "success");
        } catch (error) {
            showToast("Gagal memuat library pembuat Excel.", "error");
        }
    };

    const fileInputRef = useRef(null);
    const handleImportClick = () => fileInputRef.current.click();

    const handleFileChange = async (e) => {
        const file = e.target.files[0];
        if (!file) return;
        try {
            const XLSX = await import('https://esm.sh/xlsx@0.18.5');
            const reader = new FileReader();
            reader.onload = async (evt) => {
                try {
                    const data = evt.target.result;
                    const wb = XLSX.read(data, {type:'binary'});
                    const ws = wb.Sheets[wb.SheetNames[0]];
                    const json = XLSX.utils.sheet_to_json(ws);
                    
                    let newData = [];
                    json.forEach(row => {
                        const getVal = (key) => row[key] || row[key.toLowerCase()] || row[Object.keys(row).find(k => k.toLowerCase() === key.toLowerCase())];
                        if (tab === 'siswa') newData.push({ id: generateId(), name: getVal("Nama Lengkap"), nis: getVal("NIS"), gender: getVal("L/P"), class: getVal("Kelas"), status: getVal("Status") || 'Aktif' });
                        if (tab === 'guru') newData.push({ id: generateId(), name: getVal("Nama Guru"), nip: getVal("NIP"), mapel: getVal("Mapel"), status: getVal("Tugas Tambahan") || '-' });
                        if (tab === 'kelas') newData.push({ id: generateId(), name: getVal("Nama Kelas"), wali: getVal("Wali Kelas"), total: 0 });
                        if (tab === 'mapel') newData.push({ id: generateId(), code: getVal("Kode"), name: getVal("Nama Mapel"), kktp: getVal("KKTP") || '75' });
                        if (tab === 'jadwal') newData.push({ id: generateId(), day: getVal("Hari"), jamKe: getVal("Jam Ke"), time: calculateJamTime(getVal("Jam Ke")), class: getVal("Kelas"), subject: getVal("Mapel"), teacherName: getVal("Guru"), room: getVal("Ruang") });
                    });
                    
                    const filteredData = newData.filter(item => item && (item.name || item.code || item.day));
                    if (filteredData.length > 0) {
                        if (tab === 'siswa') await setStudents(p => [...(p || []), ...filteredData]);
                        if (tab === 'guru') await setTeachers(p => [...(p || []), ...filteredData]);
                        if (tab === 'kelas') await setClasses(p => [...(p || []), ...filteredData]);
                        if (tab === 'mapel') await setSubjects(p => [...(p || []), ...filteredData]);
                        if (tab === 'jadwal') await setSchedules(p => [...(p || []), ...filteredData]);
                        showToast(`Berhasil mengimpor ${filteredData.length} data ke database!`);
                    } else {
                        showToast("Data kosong atau format Excel tidak sesuai template.", "error");
                    }
                } catch(err) {
                    showToast("Terjadi kesalahan saat memproses file.", "error");
                }
            };
            reader.readAsBinaryString(file);
        } catch(e) {
            showToast("Gagal memuat library.", "error");
        }
        e.target.value = null; 
    };

    const backupFileInputRef = useRef(null);

    const handleExportBackup = () => {
        const backupData = {
            teachers, students, classes, subjects, schedules, jurnals,
            teacherAttendance, classLogs, accounts, attendance,
            teacherDriveLinks, schoolConfig, schoolDocs
        };
        const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(backupData));
        const downloadAnchorNode = document.createElement('a');
        downloadAnchorNode.setAttribute("href", dataStr);
        downloadAnchorNode.setAttribute("download", "sijaga_backup_" + new Date().toISOString().split('T')[0] + ".json");
        document.body.appendChild(downloadAnchorNode);
        downloadAnchorNode.click();
        downloadAnchorNode.remove();
        showToast('File backup berhasil diunduh!', 'success');
    };

    const handleImportBackupClick = () => backupFileInputRef.current.click();

    const handleImportBackupChange = (e) => {
        const file = e.target.files[0];
        if (!file) return;
        const reader = new FileReader();
        reader.onload = async (evt) => {
            try {
                const data = JSON.parse(evt.target.result);
                showConfirm('Peringatan: Seluruh data saat ini akan ditimpa dengan data dari file backup. Apakah Anda yakin?', async () => {
                    try {
                        if (data.teachers) await setTeachers(data.teachers);
                        if (data.students) await setStudents(data.students);
                        if (data.classes) await setClasses(data.classes);
                        if (data.subjects) await setSubjects(data.subjects);
                        if (data.schedules) await setSchedules(data.schedules);
                        if (data.jurnals) await setJurnals(data.jurnals);
                        if (data.teacherAttendance) await setTeacherAttendance(data.teacherAttendance);
                        if (data.classLogs) await setClassLogs(data.classLogs);
                        if (data.accounts) await setAccounts(data.accounts);
                        if (data.attendance) await setAttendance(data.attendance);
                        if (data.teacherDriveLinks) await setTeacherDriveLinks(data.teacherDriveLinks);
                        if (data.schoolConfig) await setSchoolConfig(data.schoolConfig);
                        if (data.schoolDocs) await setSchoolDocs(data.schoolDocs);
                        showToast('Data berhasil dipulihkan secara menyeluruh dari backup!', 'success');
                    } catch(err) {
                        showToast('Terjadi kesalahan saat memulihkan data.', 'error');
                    }
                });
            } catch (err) {
                showToast('File backup tidak valid atau rusak.', 'error');
            }
        };
        reader.readAsText(file);
        e.target.value = null;
    };

    const handleDeleteSingle = (id) => {
        showConfirm(`Yakin ingin menghapus baris data ini?`, async () => {
            try {
                if (tab === 'siswa') await setStudents(p => (p || []).filter(x => x.id !== id));
                if (tab === 'guru') await setTeachers(p => (p || []).filter(x => x.id !== id));
                if (tab === 'kelas') await setClasses(p => (p || []).filter(x => x.id !== id));
                if (tab === 'mapel') await setSubjects(p => (p || []).filter(x => x.id !== id));
                if (tab === 'jadwal') await setSchedules(p => (p || []).filter(x => x.id !== id));
                showToast("Data berhasil dihapus.", "success");
            } catch (err) {
                showToast("Gagal menghapus data.", "error");
            }
        });
    };

    const handleBulkDelete = () => {
        showConfirm(`Yakin ingin menghapus ${selectedIds.length} data terpilih secara permanen?`, async () => {
            try {
                if (tab === 'siswa') await setStudents(p => (p || []).filter(x => !selectedIds.includes(x.id)));
                if (tab === 'guru') await setTeachers(p => (p || []).filter(x => !selectedIds.includes(x.id)));
                if (tab === 'kelas') await setClasses(p => (p || []).filter(x => !selectedIds.includes(x.id)));
                if (tab === 'mapel') await setSubjects(p => (p || []).filter(x => !selectedIds.includes(x.id)));
                if (tab === 'jadwal') await setSchedules(p => (p || []).filter(x => !selectedIds.includes(x.id)));
                setSelectedIds([]);
                showToast("Data terpilih berhasil dihapus dari database.", "success");
            } catch (err) {
                showToast("Gagal menghapus data massal.", "error");
            }
        });
    };

    // --- FUNGSI TAMBAH & EDIT DATA ---
    const handleAddClick = () => {
        setEditingItem(null); // Set null menandakan kita sedang mode Tambah, bukan Edit
        setFormData({}); // Kosongkan form
        setShowEditModal(true);
    };

    const handleEditClick = (item) => {
        setEditingItem(item);
        setFormData({ ...item });
        setShowEditModal(true);
    };

    const handleSaveEdit = async () => {
        try {
            const isEditing = !!editingItem;
            const newItem = { ...formData, id: isEditing ? editingItem.id : generateId() };

            const updateData = (p) => {
                const arr = p || [];
                if (isEditing) {
                    return arr.map(x => x.id === editingItem.id ? { ...x, ...formData } : x);
                } else {
                    return [...arr, newItem];
                }
            };

            if (tab === 'siswa') {
                await setStudents(updateData);
            } else if (tab === 'guru') {
                await setTeachers(updateData);
            } else if (tab === 'kelas') {
                await setClasses(updateData);
            } else if (tab === 'mapel') {
                await setSubjects(updateData);
            } else if (tab === 'jadwal') {
                await setSchedules(updateData);
            }
            
            setShowEditModal(false);
            setEditingItem(null);
            setFormData({});
            showToast(`Data ${tab} berhasil ${isEditing ? 'diperbarui' : 'ditambahkan'}!`, "success");
        } catch (error) {
            showToast("Gagal menyimpan perubahan.", "error");
        }
    };

    const toggleSelect = (id) => {
        setSelectedIds(prev => prev.includes(id) ? prev.filter(x => x !== id) : [...prev, id]);
    };

    const toggleSelectAll = (items) => {
        if (selectedIds.length === items.length) setSelectedIds([]);
        else setSelectedIds((items || []).map(i => i.id));
    };

    const CheckboxCell = ({ id }) => (
        <td className="px-4 py-3 w-10 text-center">
            <input type="checkbox" checked={selectedIds.includes(id)} onChange={() => toggleSelect(id)} className="w-4 h-4 text-indigo-600 rounded border-slate-300 focus:ring-indigo-500 cursor-pointer" />
        </td>
    );

    const HeaderCheckbox = ({ items }) => (
        <th className="px-4 py-4 w-10 text-center">
            <input type="checkbox" checked={selectedIds.length === (items || []).length && (items || []).length > 0} onChange={() => toggleSelectAll(items || [])} className="w-4 h-4 text-indigo-600 rounded border-slate-300 focus:ring-indigo-500 cursor-pointer" />
        </th>
    );

    const handleSaveSchoolConfig = async () => {
        try {
            await setSchoolConfig(localSchoolConfig);
            showToast("Konfigurasi dan Logo Sekolah berhasil divalidasi & disimpan ke Database!");
        } catch (e) {
            showToast("Gagal menyimpan konfigurasi", "error");
        }
    };

    return (
        <div className="space-y-6 relative">
            {/* MODAL EDIT & TAMBAH DATA */}
            {showEditModal && (
                <div className="fixed inset-0 z-[80] flex items-center justify-center modal-overlay p-4">
                    <div className="bg-white rounded-2xl shadow-2xl w-full max-w-md p-6 md:p-8 animate-fade-in-down">
                        <div className="flex justify-between items-center mb-6">
                            <h3 className="text-xl font-bold text-slate-800 capitalize">
                                {editingItem ? `Edit Data ${tab}` : `Tambah Data ${tab}`}
                            </h3>
                            <button onClick={() => setShowEditModal(false)} className="text-slate-400 hover:text-slate-600"><X size={24} /></button>
                        </div>
                        
                        <div className="space-y-4">
                            {tab === 'siswa' && (
                                <>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Nama Lengkap</label><input type="text" value={formData.name || ''} onChange={e => setFormData({...formData, name: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">NIS</label><input type="text" value={formData.nis || ''} onChange={e => setFormData({...formData, nis: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div className="grid grid-cols-2 gap-4">
                                        <div><label className="block text-sm font-bold text-slate-700 mb-1">Kelas</label><input type="text" value={formData.class || ''} onChange={e => setFormData({...formData, class: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                        <div><label className="block text-sm font-bold text-slate-700 mb-1">L/P</label><input type="text" value={formData.gender || ''} onChange={e => setFormData({...formData, gender: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    </div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Status</label><select value={formData.status || 'Aktif'} onChange={e => setFormData({...formData, status: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none"><option value="Aktif">Aktif</option><option value="Pindah">Pindah</option><option value="Lulus">Lulus</option></select></div>
                                </>
                            )}
                            {tab === 'guru' && (
                                <>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Nama Guru</label><input type="text" value={formData.name || ''} onChange={e => setFormData({...formData, name: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">NIP</label><input type="text" value={formData.nip || ''} onChange={e => setFormData({...formData, nip: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Mapel</label><input type="text" value={formData.mapel || ''} onChange={e => setFormData({...formData, mapel: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Tugas Tambahan</label><input type="text" value={formData.status || ''} onChange={e => setFormData({...formData, status: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                </>
                            )}
                            {tab === 'kelas' && (
                                <>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Nama Kelas</label><input type="text" value={formData.name || ''} onChange={e => setFormData({...formData, name: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Wali Kelas</label><input type="text" value={formData.wali || ''} onChange={e => setFormData({...formData, wali: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                </>
                            )}
                            {tab === 'mapel' && (
                                <>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Kode</label><input type="text" value={formData.code || ''} onChange={e => setFormData({...formData, code: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Nama Mata Pelajaran</label><input type="text" value={formData.name || ''} onChange={e => setFormData({...formData, name: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">KKTP</label><input type="text" value={formData.kktp || ''} onChange={e => setFormData({...formData, kktp: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                </>
                            )}
                            {tab === 'jadwal' && (
                                <>
                                    <div className="grid grid-cols-2 gap-4">
                                        <div><label className="block text-sm font-bold text-slate-700 mb-1">Hari</label><input type="text" value={formData.day || ''} onChange={e => setFormData({...formData, day: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                        <div><label className="block text-sm font-bold text-slate-700 mb-1">Jam Ke- (Cth: 1-2)</label><input type="text" value={formData.jamKe || ''} onChange={e => { const val = e.target.value; setFormData({...formData, jamKe: val, time: calculateJamTime(val)}) }} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" placeholder="1-2" />
                                            <p className="text-xs font-bold text-indigo-600 mt-1">Waktu: {formData.time || '-'}</p>
                                        </div>
                                    </div>
                                    <div className="grid grid-cols-2 gap-4">
                                        <div><label className="block text-sm font-bold text-slate-700 mb-1">Kelas</label><input type="text" value={formData.class || ''} onChange={e => setFormData({...formData, class: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                        <div><label className="block text-sm font-bold text-slate-700 mb-1">Ruang</label><input type="text" value={formData.room || ''} onChange={e => setFormData({...formData, room: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    </div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Mapel</label><input type="text" value={formData.subject || ''} onChange={e => setFormData({...formData, subject: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                    <div><label className="block text-sm font-bold text-slate-700 mb-1">Guru</label><input type="text" value={formData.teacherName || ''} onChange={e => setFormData({...formData, teacherName: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                </>
                            )}
                        </div>
                        <div className="mt-8 flex justify-end gap-3">
                            <button onClick={() => setShowEditModal(false)} className="px-6 py-2.5 rounded-xl bg-slate-100 text-slate-700 font-bold hover:bg-slate-200 transition-colors">Batal</button>
                            <button onClick={handleSaveEdit} className="px-6 py-2.5 rounded-xl bg-indigo-600 text-white font-bold hover:bg-indigo-700 shadow-md shadow-indigo-200 transition-all flex items-center gap-2"><Save size={16} /> Simpan Data</button>
                        </div>
                    </div>
                </div>
            )}

            <div className="flex gap-2 overflow-x-auto border-b pb-2">
                {['siswa', 'guru', 'kelas', 'mapel', 'jadwal', 'sekolah', 'backup'].map(t => (
                    <button key={t} onClick={() => setTab(t)} className={`px-5 py-3 font-bold text-sm rounded-t-xl capitalize transition-all ${tab === t ? 'bg-indigo-600 text-white shadow-md' : 'bg-white text-slate-500 hover:bg-slate-100'}`}>
                        {t}
                    </button>
                ))}
            </div>
            
            <div className="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm min-h-[400px] animate-fade-in">
                {(tab !== 'sekolah' && tab !== 'backup') && (
                    <div className="flex flex-col md:flex-row justify-between items-start md:items-center mb-6 gap-4">
                        <div className="flex items-center gap-3">
                            <h3 className="font-bold text-xl text-slate-800 capitalize">Manajemen {tab}</h3>
                            {selectedIds.length > 0 && (
                                <button onClick={handleBulkDelete} className="bg-red-100 text-red-700 px-3 py-1.5 rounded-lg text-xs font-bold hover:bg-red-200 flex items-center gap-2 animate-fade-in"><Trash2 size={14}/> Hapus Terpilih ({selectedIds.length})</button>
                            )}
                        </div>
                        <div className="flex flex-wrap gap-2 w-full md:w-auto">
                            <input type="file" ref={fileInputRef} style={{display: 'none'}} accept=".xlsx, .xls" onChange={handleFileChange} />
                            <button onClick={() => handleDownloadTemplate(tab)} className="px-4 py-2 bg-slate-100 text-slate-700 rounded-xl text-sm font-bold hover:bg-slate-200 flex items-center gap-2 transition-colors"><FileSpreadsheet size={16} /> Unduh Template</button>
                            <button onClick={handleImportClick} className="px-4 py-2 bg-emerald-100 text-emerald-700 rounded-xl text-sm font-bold hover:bg-emerald-200 flex items-center gap-2 transition-colors"><Upload size={16} /> Import Excel</button>
                            <button onClick={handleAddClick} className="px-4 py-2 bg-indigo-600 text-white rounded-xl text-sm font-bold hover:bg-indigo-700 flex items-center gap-2 transition-colors shadow-md shadow-indigo-200"><Plus size={16} /> Tambah Manual</button>
                        </div>
                    </div>
                )}

                <div className="overflow-x-auto rounded-xl border border-slate-100">
                    {tab === 'siswa' && (
                        <table className="w-full text-sm text-left"><thead className="bg-slate-50 border-b"><tr><HeaderCheckbox items={students} /><th className="p-4 font-bold text-slate-700">Nama Lengkap</th><th className="p-4 font-bold text-slate-700">NIS</th><th className="p-4 font-bold text-slate-700">Kelas</th><th className="p-4 font-bold text-slate-700">L/P</th><th className="p-4 text-right font-bold text-slate-700">Aksi</th></tr></thead><tbody className="divide-y">
                            {(students || []).map(s => (<tr key={s.id} className="hover:bg-slate-50"><CheckboxCell id={s.id}/><td className="p-4 font-bold">{s.name}</td><td className="p-4 font-mono text-slate-500">{s.nis}</td><td className="p-4"><span className="px-2 py-1 bg-slate-100 rounded text-xs font-bold">{s.class}</span></td><td className="p-4">{s.gender}</td><td className="p-4 text-right"><div className="flex justify-end gap-1"><button onClick={()=> handleEditClick(s)} className="p-2 text-indigo-500 hover:bg-indigo-50 rounded-lg"><Edit size={16}/></button><button onClick={()=> handleDeleteSingle(s.id)} className="p-2 text-red-500 hover:bg-red-50 rounded-lg"><Trash2 size={16}/></button></div></td></tr>))}
                        </tbody></table>
                    )}
                    {tab === 'guru' && (
                        <table className="w-full text-sm text-left"><thead className="bg-slate-50 border-b"><tr><HeaderCheckbox items={teachers} /><th className="p-4 font-bold text-slate-700">Nama Guru</th><th className="p-4 font-bold text-slate-700">NIP</th><th className="p-4 font-bold text-slate-700">Mapel</th><th className="p-4 text-right font-bold text-slate-700">Aksi</th></tr></thead><tbody className="divide-y">
                            {(teachers || []).map(t => (<tr key={t.id} className="hover:bg-slate-50"><CheckboxCell id={t.id}/><td className="p-4 font-bold">{t.name}</td><td className="p-4 font-mono text-slate-500">{t.nip}</td><td className="p-4">{t.mapel}</td><td className="p-4 text-right"><div className="flex justify-end gap-1"><button onClick={()=> handleEditClick(t)} className="p-2 text-indigo-500 hover:bg-indigo-50 rounded-lg"><Edit size={16}/></button><button onClick={()=> handleDeleteSingle(t.id)} className="p-2 text-red-500 hover:bg-red-50 rounded-lg"><Trash2 size={16}/></button></div></td></tr>))}
                        </tbody></table>
                    )}
                    {tab === 'kelas' && (
                        <table className="w-full text-sm text-left"><thead className="bg-slate-50 border-b"><tr><HeaderCheckbox items={classes} /><th className="p-4 font-bold text-slate-700">Nama Kelas</th><th className="p-4 font-bold text-slate-700">Wali Kelas</th><th className="p-4 text-right font-bold text-slate-700">Aksi</th></tr></thead><tbody className="divide-y">
                            {(classes || []).map(c => (<tr key={c.id} className="hover:bg-slate-50"><CheckboxCell id={c.id}/><td className="p-4 font-bold text-lg">{c.name}</td><td className="p-4 text-slate-600">{c.wali}</td><td className="p-4 text-right"><div className="flex justify-end gap-1"><button onClick={()=> handleEditClick(c)} className="p-2 text-indigo-500 hover:bg-indigo-50 rounded-lg"><Edit size={16}/></button><button onClick={()=> handleDeleteSingle(c.id)} className="p-2 text-red-500 hover:bg-red-50 rounded-lg"><Trash2 size={16}/></button></div></td></tr>))}
                        </tbody></table>
                    )}
                    {tab === 'mapel' && (
                        <table className="w-full text-sm text-left"><thead className="bg-slate-50 border-b"><tr><HeaderCheckbox items={subjects} /><th className="p-4 font-bold text-slate-700">Kode</th><th className="p-4 font-bold text-slate-700">Nama Mata Pelajaran</th><th className="p-4 font-bold text-slate-700">KKTP</th><th className="p-4 text-right font-bold text-slate-700">Aksi</th></tr></thead><tbody className="divide-y">
                            {(subjects || []).map(s => (<tr key={s.id} className="hover:bg-slate-50"><CheckboxCell id={s.id}/><td className="p-4 font-mono font-bold text-indigo-600">{s.code}</td><td className="p-4 font-bold">{s.name}</td><td className="p-4">{s.kktp}</td><td className="p-4 text-right"><div className="flex justify-end gap-1"><button onClick={()=> handleEditClick(s)} className="p-2 text-indigo-500 hover:bg-indigo-50 rounded-lg"><Edit size={16}/></button><button onClick={()=> handleDeleteSingle(s.id)} className="p-2 text-red-500 hover:bg-red-50 rounded-lg"><Trash2 size={16}/></button></div></td></tr>))}
                        </tbody></table>
                    )}
                    {tab === 'jadwal' && (
                        <table className="w-full text-sm text-left"><thead className="bg-slate-50 border-b"><tr><HeaderCheckbox items={schedules} /><th className="p-4 font-bold text-slate-700">Hari</th><th className="p-4 font-bold text-slate-700">Jam Ke</th><th className="p-4 font-bold text-slate-700">Waktu</th><th className="p-4 font-bold text-slate-700">Kelas</th><th className="p-4 font-bold text-slate-700">Mapel</th><th className="p-4 font-bold text-slate-700">Guru</th><th className="p-4 text-right font-bold text-slate-700">Aksi</th></tr></thead><tbody className="divide-y">
                            {(schedules || []).map(s => (<tr key={s.id} className="hover:bg-slate-50"><CheckboxCell id={s.id}/><td className="p-4 font-bold">{s.day}</td><td className="p-4 font-bold text-indigo-600">{s.jamKe || '-'}</td><td className="p-4 text-slate-500 font-mono">{s.time}</td><td className="p-4"><span className="px-2 py-1 bg-slate-100 rounded text-xs font-bold">{s.class}</span></td><td className="p-4">{s.subject}</td><td className="p-4 text-slate-600">{s.teacherName}</td><td className="p-4 text-right"><div className="flex justify-end gap-1"><button onClick={()=> handleEditClick(s)} className="p-2 text-indigo-500 hover:bg-indigo-50 rounded-lg"><Edit size={16}/></button><button onClick={()=> handleDeleteSingle(s.id)} className="p-2 text-red-500 hover:bg-red-50 rounded-lg"><Trash2 size={16}/></button></div></td></tr>))}
                        </tbody></table>
                    )}
                </div>

                {tab === 'sekolah' && (
                    <div className="max-w-2xl bg-slate-50 p-6 rounded-2xl border border-slate-200">
                        <div className="flex items-center gap-4 mb-6 pb-6 border-b border-slate-200">
                            <div className="w-24 h-24 rounded-xl border-4 border-white shadow-md overflow-hidden bg-white shrink-0">
                                {localSchoolConfig?.logo ? <img src={localSchoolConfig.logo} alt="Logo Sekolah" className="w-full h-full object-cover" onError={(e) => {e.target.onerror = null; e.target.src = 'https://via.placeholder.com/150?text=No+Logo'}} /> : <div className="w-full h-full flex items-center justify-center bg-gray-100 text-gray-400">Logo</div>}
                            </div>
                            <div className="flex-1">
                                <label className="block text-sm font-bold text-slate-700 mb-1">URL Logo Sekolah</label>
                                <input type="text" value={localSchoolConfig.logo || ''} onChange={e => setLocalSchoolConfig({...localSchoolConfig, logo: e.target.value})} placeholder="https://..." className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none text-sm" />
                                <p className="text-xs text-slate-500 mt-1">Logo ini akan otomatis digunakan di halaman Login setelah disimpan.</p>
                            </div>
                        </div>
                        <div className="space-y-5">
                            <div><label className="block text-sm font-bold text-slate-700 mb-1">Nama Sekolah</label><input value={localSchoolConfig.name || ''} onChange={e=>setLocalSchoolConfig({...localSchoolConfig, name: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                            <div><label className="block text-sm font-bold text-slate-700 mb-1">Alamat Lengkap</label><textarea value={localSchoolConfig.address || ''} onChange={e=>setLocalSchoolConfig({...localSchoolConfig, address: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" rows="2" placeholder="Cth: Jl. Pendidikan No. 1..." /></div>
                            <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
                                <div><label className="block text-sm font-bold text-slate-700 mb-1">NPSN</label><input value={localSchoolConfig.npsn || ''} onChange={e=>setLocalSchoolConfig({...localSchoolConfig, npsn: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                <div><label className="block text-sm font-bold text-slate-700 mb-1">Tahun Ajaran</label><input value={localSchoolConfig.academicYear || ''} onChange={e=>setLocalSchoolConfig({...localSchoolConfig, academicYear: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" /></div>
                                <div><label className="block text-sm font-bold text-slate-700 mb-1">Email Sekolah</label><input type="email" value={localSchoolConfig.email || ''} onChange={e=>setLocalSchoolConfig({...localSchoolConfig, email: e.target.value})} className="w-full p-3 border border-slate-300 rounded-xl focus:ring-indigo-500 outline-none" placeholder="info@sekolah.sch.id" /></div>
                            </div>
                            <div className="pt-4 flex justify-end">
                                <button onClick={handleSaveSchoolConfig} className="bg-indigo-600 text-white px-8 py-3 rounded-xl font-bold hover:bg-indigo-700 shadow-lg shadow-indigo-200 flex items-center gap-2 transition-all transform hover:-translate-y-1">
                                    <Save size={18} /> Simpan ke Database
                                </button>
                            </div>
                        </div>
                    </div>
                )}

                {tab === 'backup' && (
                    <div className="max-w-2xl bg-slate-50 p-6 rounded-2xl border border-slate-200 animate-fade-in">
                        <div className="flex items-center gap-4 mb-6 pb-6 border-b border-slate-200">
                            <div className="w-16 h-16 rounded-xl bg-indigo-100 text-indigo-600 flex items-center justify-center shrink-0">
                                <Database size={32} />
                            </div>
                            <div>
                                <h3 className="text-xl font-bold text-slate-800">Backup & Pemulihan Data</h3>
                                <p className="text-sm text-slate-500 mt-1">Simpan seluruh data aplikasi atau kembalikan data dari file backup (.json).</p>
                            </div>
                        </div>
                        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div className="bg-white p-6 rounded-xl border border-slate-200 shadow-sm flex flex-col items-center text-center transition-transform hover:scale-[1.02]">
                                <div className="p-4 bg-emerald-50 text-emerald-600 rounded-full mb-4"><Download size={24} /></div>
                                <h4 className="font-bold text-slate-800 mb-2">Export Backup</h4>
                                <p className="text-xs text-slate-500 mb-6">Unduh semua data (Siswa, Guru, Jadwal, Jurnal, dll) ke dalam satu file .json yang aman.</p>
                                <button onClick={handleExportBackup} className="w-full bg-emerald-600 text-white py-2.5 rounded-lg font-bold hover:bg-emerald-700 shadow-md shadow-emerald-200 transition-colors flex items-center justify-center gap-2">
                                    <Download size={16} /> Download Backup
                                </button>
                            </div>
                            <div className="bg-white p-6 rounded-xl border border-slate-200 shadow-sm flex flex-col items-center text-center transition-transform hover:scale-[1.02]">
                                <div className="p-4 bg-orange-50 text-orange-600 rounded-full mb-4"><Upload size={24} /></div>
                                <h4 className="font-bold text-slate-800 mb-2">Restore Backup</h4>
                                <p className="text-xs text-slate-500 mb-6">Kembalikan semua data dari file .json. <strong className="text-red-500">Perhatian:</strong> Data saat ini akan tertimpa!</p>
                                <input type="file" ref={backupFileInputRef} style={{display: 'none'}} accept=".json" onChange={handleImportBackupChange} />
                                <button onClick={handleImportBackupClick} className="w-full bg-orange-600 text-white py-2.5 rounded-lg font-bold hover:bg-orange-700 shadow-md shadow-orange-200 transition-colors flex items-center justify-center gap-2">
                                    <Upload size={16} /> Pilih File Backup
                                </button>
                            </div>
                        </div>
                    </div>
                )}
            </div>
        </div>
    );
};

// --- APP UTAMA ---
export default function App() {
    const [fbUser, setFbUser] = useState(null);
    const [user, setUser] = useState(null);
    const [activeTab, setActiveTab] = useState('dashboard');
    const [isSidebarOpen, setIsSidebarOpen] = useState(false);
    const [toast, setToast] = useState(null);
    const [confirm, setConfirm] = useState(null);

    useEffect(() => {
        const initAuth = async () => {
            try {
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }
            } catch (e) {
                console.error("Auth error", e);
            }
        };
        initAuth();
        const unsubscribe = onAuthStateChanged(auth, (u) => setFbUser(u));
        return () => unsubscribe();
    }, []);

    // Load semua state Firebase dengan default aman
    const [teachers, setTeachers] = useFirebaseData('teachers', INITIAL_TEACHERS, fbUser);
    const [students, setStudents] = useFirebaseData('students', INITIAL_STUDENTS, fbUser);
    const [classes, setClasses] = useFirebaseData('classes', INITIAL_CLASSES, fbUser);
    const [subjects, setSubjects] = useFirebaseData('subjects', INITIAL_SUBJECTS, fbUser);
    const [schedules, setSchedules] = useFirebaseData('schedules', INITIAL_SCHEDULE, fbUser);
    const [jurnals, setJurnals] = useFirebaseData('jurnals', [], fbUser);
    const [teacherAttendance, setTeacherAttendance] = useFirebaseData('teacherAttendance', [], fbUser);
    const [classLogs, setClassLogs] = useFirebaseData('classLogs', [], fbUser);
    const [accounts, setAccounts] = useFirebaseData('accounts', INITIAL_ACCOUNTS, fbUser);
    const [attendance, setAttendance] = useFirebaseData('attendance', {}, fbUser); 
    const [teacherDriveLinks, setTeacherDriveLinks] = useFirebaseData('teacherDriveLinks', INITIAL_DRIVE_LINKS, fbUser);
    const [schoolConfig, setSchoolConfig] = useFirebaseData('schoolConfig', INITIAL_SCHOOL_CONFIG, fbUser);
    const [schoolDocs, setSchoolDocs] = useFirebaseData('schoolDocs', INITIAL_SCHOOL_DOCS, fbUser);

    const showToast = (message, type = 'success') => { setToast({ message, type }); setTimeout(() => setToast(null), 3000); };
    const showConfirm = (message, onConfirm) => { setConfirm({ message, onConfirm: () => { onConfirm(); setConfirm(null); }, onCancel: () => setConfirm(null) }); };

    if (!user) return <><LoginScreen onLogin={setUser} accounts={accounts || []} showToast={showToast} schoolConfig={schoolConfig || {}} /><ToastContainer toast={toast} /></>;

    const currentTeacher = user?.role === 'guru' ? (teachers || []).find(t => t.name === user.name) : null; 
    const isPiket = currentTeacher?.status?.includes('Guru Piket');
    const isWaliKelas = currentTeacher?.status?.includes('Wali Kelas');
    const managedClass = isWaliKelas ? (classes || []).find(c => c.wali === user?.name)?.name : null;
    const isManagement = user?.role === 'admin' || user?.role === 'kepala_sekolah' || currentTeacher?.status?.includes('Kepala Sekolah') || currentTeacher?.status?.includes('Wakil Kepala Sekolah');

    return (
        <div className="flex h-screen bg-slate-50 overflow-hidden font-sans selection:bg-indigo-100 selection:text-indigo-700">
            <Sidebar activeTab={activeTab} setActiveTab={setActiveTab} isOpen={isSidebarOpen} setIsOpen={setIsSidebarOpen} user={user} onLogout={() => setUser(null)} isPiket={isPiket} isManagement={isManagement} isWaliKelas={isWaliKelas} schoolConfig={schoolConfig || {}} />
            
            <div className="flex-1 flex flex-col min-w-0 overflow-hidden relative">
                <header className="h-20 glass-header border-b border-slate-200 flex items-center justify-between px-6 z-30 sticky top-0 bg-white/90 backdrop-blur-md">
                    <div className="flex items-center gap-4">
                        <button onClick={() => setIsSidebarOpen(true)} className="md:hidden text-slate-500 hover:text-slate-800"><Menu size={24} /></button>
                        <div>
                            <h1 className="text-xl font-bold text-slate-800 hidden md:block">{schoolConfig?.name || 'SIJAGA'}</h1>
                            <div className="text-xs text-slate-500 hidden md:flex gap-2"><span>NPSN: {schoolConfig?.npsn || '-'}</span><span>•</span><span className="text-indigo-600">{schoolConfig?.academicYear || '-'} ({schoolConfig?.semester || '-'})</span></div>
                        </div>
                    </div>
                    <div className="w-10 h-10 rounded-full bg-gradient-to-tr from-indigo-500 to-purple-500 flex items-center justify-center text-white font-bold shadow-md cursor-default" title={user.name}>{user.name.charAt(0).toUpperCase()}</div>
                </header>
                
                <main className="flex-1 overflow-y-auto p-4 md:p-8 no-scrollbar bg-slate-50/50">
                    {activeTab === 'dashboard' && <Dashboard user={user} teachersCount={(teachers || []).length} studentsCount={(students || []).length} setActiveTab={setActiveTab} classLogs={classLogs || []} setClassLogs={setClassLogs} teacherAttendance={teacherAttendance || []} schedules={schedules || []} jurnals={jurnals || []} showToast={showToast} isManagement={isManagement} />}
                    {activeTab === 'absensi-guru' && <AbsensiGuru user={user} teacherAttendance={teacherAttendance || []} setTeacherAttendance={setTeacherAttendance} classLogs={classLogs || []} setClassLogs={setClassLogs} schedules={schedules || []} showToast={showToast} />}
                    {activeTab === 'jurnal' && <JurnalMengajar user={user} schedules={schedules || []} students={students || []} attendance={attendance || {}} jurnals={jurnals || []} setJurnals={setJurnals} showToast={showToast} schoolConfig={schoolConfig || {}} teachers={teachers || []} />}
                    {activeTab === 'drive-guru' && <DriveAdministrasiGuru teacherDriveLinks={teacherDriveLinks || {}} setTeacherDriveLinks={setTeacherDriveLinks} user={user} showToast={showToast} />}
                    {activeTab === 'presensi' && <PresensiSiswa students={students || []} attendance={attendance || {}} setAttendance={setAttendance} showToast={showToast} user={user} schedules={schedules || []} classes={classes || []} />}
                    {activeTab === 'p5' && <JurnalKokurikuler showToast={showToast} />}
                    {activeTab === 'sk-kbm' && <DokumenView title="SK Pembagian Tugas (KBM)" type="sk_kbm" schoolDocs={schoolDocs || {}} />}
                    {activeTab === 'pekan-efektif' && <DokumenView title="Perhitungan Pekan Efektif" type="pekan_efektif" schoolDocs={schoolDocs || {}} />}
                    {activeTab === 'monitoring' && <MonitoringGuru teacherAttendance={teacherAttendance || []} classLogs={classLogs || []} schedules={schedules || []} jurnals={jurnals || []} teachers={teachers || []} />}
                    {activeTab === 'analisis-siswa' && <AnalisisSiswa classes={classes || []} students={students || []} attendance={attendance || {}} jurnals={jurnals || []} schedules={schedules || []} user={user} isWaliKelas={isWaliKelas} managedClass={managedClass} isManagement={isManagement} />}
                    {activeTab === 'data' && <ManajemenData teachers={teachers || []} setTeachers={setTeachers} students={students || []} setStudents={setStudents} classes={classes || []} setClasses={setClasses} subjects={subjects || []} setSubjects={setSubjects} schedules={schedules || []} setSchedules={setSchedules} showConfirm={showConfirm} showToast={showToast} teacherDriveLinks={teacherDriveLinks || {}} setTeacherDriveLinks={setTeacherDriveLinks} schoolConfig={schoolConfig || {}} setSchoolConfig={setSchoolConfig} schoolDocs={schoolDocs || {}} setSchoolDocs={setSchoolDocs} jurnals={jurnals || []} setJurnals={setJurnals} teacherAttendance={teacherAttendance || []} setTeacherAttendance={setTeacherAttendance} classLogs={classLogs || []} setClassLogs={setClassLogs} accounts={accounts || []} setAccounts={setAccounts} attendance={attendance || {}} setAttendance={setAttendance} />}
                    {activeTab === 'generate-akun' && <GenerateAkun teachers={teachers || []} accounts={accounts || []} setAccounts={setAccounts} showToast={showToast} />}
                    {activeTab === 'jadwal' && <JadwalGuru user={user} schedules={schedules || []} />}
                </main>
            </div>
            <ToastContainer toast={toast} />
            <ConfirmModal confirm={confirm} />
        </div>
    );
}