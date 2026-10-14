const homeView = document.getElementById('homeView');
const searchView = document.getElementById('searchView');
const chatView = document.getElementById('chatView');
const headerStatus = document.getElementById('headerStatus');
const messages = document.getElementById('messages');
const messageInput = document.getElementById('messageInput');
const charCount = document.getElementById('charCount');
const modalBackdrop = document.getElementById('modalBackdrop');
const modalTitle = document.getElementById('modalTitle');
const modalContent = document.getElementById('modalContent');
const toast = document.getElementById('toast');
let toastTimer;

document.getElementById('year').textContent = new Date().getFullYear();

function showView(view) {
  [homeView, searchView, chatView].forEach(v => v.classList.add('hidden'));
  view.classList.remove('hidden');
  window.scrollTo({top: 0, behavior: 'smooth'});
}
function showToast(message) {
  toast.textContent = message;
  toast.classList.remove('hidden');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => toast.classList.add('hidden'), 3200);
}
function openModal(title, html) {
  modalTitle.textContent = title;
  modalContent.innerHTML = html;
  modalBackdrop.classList.remove('hidden');
}
function closeModal() { modalBackdrop.classList.add('hidden'); }

const rulesHtml = `
<h3>Be kind</h3><p>Talk respectfully. Harassment, threats, hate, and targeted abuse are not welcome.</p>
<h3>Protect your privacy</h3><p>Don't share your address, passwords, financial details, or other sensitive personal information with strangers.</p>
<h3>Report and leave</h3><p>Use Report for abusive behaviour, Spam, threats, or other safety concerns. Use Block or Next if you don't want to continue a conversation.</p>
<h3>Prototype note</h3><p>This preview does not connect to real strangers. Reports and blocks in this demo are not sent to a moderation team.</p>`;
const termsHtml = `
<h3>1. Service</h3><p>Anjaanly is designed for random text conversations with strangers. This page is a non-production demo; live matching is not active.</p>
<h3>2. Acceptable use</h3><p>Do not harass, threaten, spam, defraud, impersonate others, share private information without permission, or use the service for unlawful purposes.</p>
<h3>3. Moderation</h3><p>A future live service may review reports, apply rate limits, restrict sessions, or suspend access under published rules. A report alone does not guarantee a ban.</p>
<h3>4. Privacy and reports</h3><p>Live-service data handling, including any evidence retained after a report, must be explained in a separate privacy policy before launch. This demo sends no reports to a server.</p>
<h3>5. Availability</h3><p>No guarantee is made that matching or messaging will always be available. The service may be changed or paused for safety, maintenance, or technical reasons.</p>
<h3>6. Updates</h3><p>Terms may change before a public launch. This draft is informational and is not legal advice.</p>`;
const privacyHtml = `
<h3>This is a demo</h3><p>This prototype runs in your browser and does not connect you to another person. Messages you type are rendered locally and are not sent to a chat server by this demo.</p>
<h3>What a live version needs</h3><p>Before launch, Anjaanly must publish a complete privacy notice explaining data collected, purpose, retention, moderation evidence, service providers, user rights, and contact details.</p>
<h3>Report evidence</h3><p>A live service may need to retain a limited part of a reported conversation for safety review, with access controls and a defined retention period. Users should be told this before using the service.</p>
<h3>Don't share sensitive details</h3><p>Even on anonymous chat services, avoid sharing passwords, exact location, financial information, or identifying details.</p>`;
function startSearch() {
  headerStatus.textContent = 'Searching (demo)';
  showView(searchView);
}
function openDemoChat() {
  headerStatus.textContent = 'Demo chat';
  showView(chatView);
  messageInput.focus({preventScroll:true});
}
document.getElementById('startBtn').addEventListener('click', startSearch);
document.getElementById('cancelSearch').addEventListener('click', () => { headerStatus.textContent = 'Ready to connect'; showView(homeView); });
document.getElementById('demoChatBtn').addEventListener('click', openDemoChat);
document.getElementById('leaveChat').addEventListener('click', () => {
  headerStatus.textContent = 'Ready to connect';
  showView(homeView);
  showToast('Demo chat ended. This preview is not connected to real users.');
});
document.getElementById('nextBtn').addEventListener('click', () => {
  messages.innerHTML = '<div class="chat-start-label">NEW CONNECTION · DEMO</div><div class="system-message">A real app would search for another available stranger here.</div>';
  startSearch();
});
document.getElementById('rulesBtn').addEventListener('click', () => openModal('Community guidelines', rulesHtml));
document.getElementById('footerRulesBtn').addEventListener('click', () => openModal('Community guidelines', rulesHtml));
document.getElementById('termsBtn').addEventListener('click', () => openModal('Terms of use · Draft', termsHtml));
document.getElementById('privacyBtn').addEventListener('click', () => openModal('Privacy · Demo notice', privacyHtml));
document.getElementById('modalClose').addEventListener('click', closeModal);
document.getElementById('modalOkay').addEventListener('click', closeModal);
modalBackdrop.addEventListener('click', e => { if (e.target === modalBackdrop) closeModal(); });
document.addEventListener('keydown', e => { if (e.key === 'Escape') closeModal(); });

document.getElementById('reportBtn').addEventListener('click', () => {
  openModal('Report this conversation', `
  <p>Choose a reason. In this demo, the report is not sent anywhere; a live version needs a secure report backend and moderation queue.</p>
  <div class="report-options">
    <label><input type="radio" name="reportReason" value="Abusive language"> Abusive language</label>
    <label><input type="radio" name="reportReason" value="Harassment"> Harassment</label>
    <label><input type="radio" name="reportReason" value="Threats"> Threats</label>
    <label><input type="radio" name="reportReason" value="Spam"> Spam</label>
    <label><input type="radio" name="reportReason" value="Other"> Other</label>
  </div>
  <button class="primary-button full-button" id="submitReport" style="margin-top:18px">Submit demo report</button>`);
  document.getElementById('submitReport').addEventListener('click', () => {
    const selected = document.querySelector('input[name="reportReason"]:checked');
    if (!selected) { showToast('Please select a reason first.'); return; }
    closeModal();
    showToast('Demo report noted locally: ' + selected.value + '. No moderator was notified.');
  });
});
document.getElementById('blockBtn').addEventListener('click', () => {
  openModal('Block this stranger?', `<p>In a live service, blocking should immediately end the match and prevent reconnecting with that user where technically possible.</p><p>In this demo, no real user is connected.</p><button class="primary-button full-button" id="confirmBlock">Block in this demo</button>`);
  document.getElementById('confirmBlock').addEventListener('click', () => {
    closeModal(); headerStatus.textContent = 'Ready to connect'; showView(homeView);
    showToast('Demo block action complete. No real user was blocked.');
  });
});

document.getElementById('messageForm').addEventListener('submit', e => {
  e.preventDefault();
  const text = messageInput.value.trim();
  if (!text) return;
  if (text.length > 500) { showToast('Please keep messages under 500 characters.'); return; }
  // This is a local UI preview only; no message is transmitted to another user.
  const row = document.createElement('div');
  row.className = 'message-row mine-row';
  const content = document.createElement('div'); content.className = 'message-content';
  const bubble = document.createElement('div'); bubble.className = 'message-bubble'; bubble.textContent = text;
  const time = document.createElement('span'); time.className = 'message-time'; time.textContent = 'Just now';
  content.append(bubble, time);
  const avatar = document.createElement('div'); avatar.className = 'message-avatar mine-avatar'; avatar.textContent = 'Y';
  row.append(content, avatar); messages.appendChild(row);
  messageInput.value = ''; charCount.textContent = '0/500'; messages.scrollTop = messages.scrollHeight;
  showToast('Preview only — this message was not sent to a stranger.');
});
messageInput.addEventListener('input', () => { charCount.textContent = `${messageInput.value.length}/500`; });
document.querySelectorAll('.suggestion-chip').forEach(btn => btn.addEventListener('click', () => {
  messageInput.value = btn.textContent; charCount.textContent = `${messageInput.value.length}/500`; messageInput.focus();
}));
