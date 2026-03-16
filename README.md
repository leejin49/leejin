<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Big Talkers 정산</title>
  <style>
    :root {
      --bg: #f6f7fb;
      --card: #ffffff;
      --line: #e5e7eb;
      --text: #111827;
      --sub: #6b7280;
      --accent: #2563eb;
      --accent-soft: #dbeafe;
      --danger: #dc2626;
      --success: #16a34a;
      --shadow: 0 10px 30px rgba(17, 24, 39, 0.08);
      --radius: 18px;
    }

    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Apple SD Gothic Neo", "Noto Sans KR", sans-serif;
      background: var(--bg);
      color: var(--text);
    }

    .wrap {
      max-width: 1200px;
      margin: 0 auto;
      padding: 24px;
    }

    .hero {
      background: linear-gradient(135deg, #1d4ed8, #2563eb 55%, #60a5fa);
      color: white;
      border-radius: 24px;
      padding: 28px;
      box-shadow: var(--shadow);
      margin-bottom: 20px;
    }

    .hero h1 {
      margin: 0 0 10px;
      font-size: 30px;
      line-height: 1.2;
    }

    .hero p {
      margin: 0;
      color: rgba(255,255,255,0.9);
      line-height: 1.6;
    }

    .grid {
      display: grid;
      grid-template-columns: 1.15fr 0.85fr;
      gap: 20px;
    }

    .card {
      background: var(--card);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 20px;
      border: 1px solid rgba(229, 231, 235, 0.9);
    }

    .card h2 {
      margin: 0 0 16px;
      font-size: 20px;
    }

    .card h3 {
      margin: 0 0 12px;
      font-size: 16px;
    }

    .section + .section {
      margin-top: 18px;
      padding-top: 18px;
      border-top: 1px solid var(--line);
    }

    .input-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 12px;
    }

    .input-grid.three {
      grid-template-columns: repeat(3, minmax(0, 1fr));
    }

    label {
      display: block;
      font-size: 13px;
      color: var(--sub);
      margin-bottom: 6px;
      font-weight: 600;
    }

    input, select, textarea {
      width: 100%;
      border: 1px solid var(--line);
      border-radius: 12px;
      padding: 12px 14px;
      font-size: 14px;
      background: white;
    }

    textarea {
      min-height: 120px;
      resize: vertical;
      line-height: 1.5;
    }

    .row {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    button {
      border: 0;
      border-radius: 12px;
      padding: 11px 16px;
      font-size: 14px;
      font-weight: 700;
      cursor: pointer;
      transition: transform 0.12s ease, opacity 0.12s ease;
    }

    button:hover { transform: translateY(-1px); }
    button:active { transform: translateY(0); }

    .primary { background: var(--accent); color: white; }
    .secondary { background: #eef2ff; color: #3730a3; }
    .ghost { background: #f3f4f6; color: #374151; }
    .danger { background: #fee2e2; color: var(--danger); }
    .success { background: #dcfce7; color: var(--success); }

    .table-list, .member-list, .expense-list, .message-list, .receipt-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .item {
      border: 1px solid var(--line);
      border-radius: 16px;
      padding: 14px;
      background: #fff;
    }

    .item-top {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 8px;
    }

    .item-title {
      font-weight: 800;
      font-size: 15px;
    }

    .muted {
      color: var(--sub);
      font-size: 13px;
      line-height: 1.5;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      border-radius: 999px;
      padding: 6px 10px;
      font-size: 12px;
      font-weight: 700;
      background: var(--accent-soft);
      color: var(--accent);
    }

    .summary-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 12px;
      margin-top: 10px;
    }

    .summary-box {
      border-radius: 16px;
      padding: 16px;
      background: #f8fafc;
      border: 1px solid var(--line);
    }

    .summary-box .label {
      font-size: 12px;
      color: var(--sub);
      margin-bottom: 6px;
      font-weight: 700;
    }

    .summary-box .value {
      font-size: 22px;
      font-weight: 900;
    }

    .empty {
      padding: 18px;
      text-align: center;
      border: 1px dashed #cbd5e1;
      border-radius: 16px;
      color: var(--sub);
      background: #f8fafc;
    }

    .preview-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 12px;
      margin-top: 12px;
    }

    .preview-card {
      border: 1px solid var(--line);
      border-radius: 14px;
      overflow: hidden;
      background: #fff;
    }

    .preview-card img {
      display: block;
      width: 100%;
      height: 180px;
      object-fit: cover;
      background: #f3f4f6;
    }

    .preview-card .meta {
      padding: 10px 12px;
      font-size: 13px;
      color: var(--sub);
    }

    .footer-note {
      margin-top: 20px;
      font-size: 13px;
      color: var(--sub);
      text-align: center;
    }

    @media (max-width: 960px) {
      .grid {
        grid-template-columns: 1fr;
      }
      .summary-grid,
      .input-grid,
      .input-grid.three,
      .preview-grid {
        grid-template-columns: 1fr;
      }
      .wrap { padding: 16px; }
      .hero { padding: 22px; }
      .hero h1 { font-size: 24px; }
    }
  </style>
</head>
<body>
  <div class="wrap">
    <section class="hero">
      <h1>Big Talkers 정산</h1>
      <p>
        날짜 선택 → 참석자와 테이블 입력 → 총 결제 금액 입력 → 테이블별 정산 메시지 복사까지 한 번에 처리하는 간단한 정산 페이지입니다.
        음료비는 영수증 사진을 첨부해두고 각자 따로 보내도록 정리할 수 있게 구성했습니다.
      </p>
    </section>

    <div class="grid">
      <main class="card">
        <h2>정산 설정</h2>

        <div class="section">
          <div class="input-grid">
            <div>
              <label for="meetingDate">날짜</label>
              <input id="meetingDate" type="date" />
            </div>
          </div>
        </div>

        <div class="section">
          <h3>참석자 추가</h3>
          <div class="input-grid">
            <div>
              <label for="memberName">이름</label>
              <input id="memberName" placeholder="예: 민수" />
            </div>
            <div>
              <label for="memberTable">테이블</label>
              <input id="memberTable" placeholder="예: A테이블" />
            </div>
          </div>
          <div class="row" style="margin-top: 12px;">
            <button class="primary" id="addMemberBtn">참석자 추가</button>
            <button class="ghost" id="sampleBtn">샘플 데이터 넣기</button>
            <button class="danger" id="resetBtn">전체 초기화</button>
          </div>
        </div>

        <div class="section">
          <h3>결제 금액</h3>
          <div class="input-grid">
            <div>
              <label for="expenseAmount">금액</label>
              <input id="expenseAmount" type="number" min="0" placeholder="예: 148000" />
            </div>
          </div>
          <div class="row" style="margin-top: 12px;">
            <button class="secondary" id="addExpenseBtn">금액 추가</button>
          </div>
          <div class="expense-list" id="expenseList" style="margin-top: 14px;"></div>
        </div>

        <div class="section">
          <h3>음료비용 영수증 첨부</h3>
          <label for="receiptInput">영수증 사진 업로드</label>
          <input id="receiptInput" type="file" accept="image/*" multiple />
          <div class="muted" style="margin-top: 8px;">
            음료는 각자 영수증 보고 따로 보내는 방식이면, 사진만 올려두고 카톡방에 같이 공유하면 가장 편합니다.
          </div>
          <div class="preview-grid" id="receiptPreview"></div>
        </div>

        <div class="section">
          <h3>음료비 메모</h3>
          <label for="drinkMemo">누가 어떤 음료를 마셨는지 간단 메모</label>
          <textarea id="drinkMemo" placeholder="예: 민수 - 아이스 아메리카노 1잔 / 서연 - 레몬에이드 1잔"></textarea>
        </div>

        <div class="section">
          <h3>참석자 목록</h3>
          <div class="member-list" id="memberList"></div>
        </div>
      </main>

      <aside class="card">
        <h2>정산 결과</h2>

        <div class="summary-grid">
          <div class="summary-box">
            <div class="label">총 참석자</div>
            <div class="value" id="totalMembers">0명</div>
          </div>
          <div class="summary-box">
            <div class="label">총 결제 금액</div>
            <div class="value" id="totalExpense">0원</div>
          </div>
          <div class="summary-box">
            <div class="label">1인당 평균</div>
            <div class="value" id="averageCost">0원</div>
          </div>
        </div>

        <div class="section">
          <h3>테이블별 정산</h3>
          <div class="table-list" id="tableList"></div>
        </div>

        <div class="section">
          <h3>카톡 복사용 메시지</h3>
          <div class="message-list" id="messageList"></div>
        </div>
      </aside>
    </div>

    <p class="footer-note">
      현재 버전은 브라우저에서 바로 쓰는 단일 HTML입니다. 다음 단계로는 저장 기능, 미입금 체크, 참석자 일괄 붙여넣기까지 확장할 수 있습니다.
    </p>
  </div>

  <script>
    const state = {
      members: [],
      expenses: [],
      receipts: []
    };

    const $ = (id) => document.getElementById(id);
    const money = (n) => `${Number(n || 0).toLocaleString('ko-KR')}원`;

    function escapeHtml(text) {
      return String(text)
        .replace(/&/g, '&amp;')
        .replace(/</g, '&lt;')
        .replace(/>/g, '&gt;')
        .replace(/\"/g, '&quot;')
        .replace(/'/g, '&#039;');
    }

    function getTables() {
      return [...new Set(state.members.map(m => m.table).filter(Boolean))];
    }

    function addMember() {
      const name = $('memberName').value.trim();
      const table = $('memberTable').value.trim();

      if (!name || !table) {
        alert('이름과 테이블은 꼭 입력해주세요.');
        return;
      }

      state.members.push({
        id: crypto.randomUUID(),
        name,
        table
      });

      $('memberName').value = '';
      $('memberTable').value = '';
      render();
    }

    function addExpense() {
      const amount = Number($('expenseAmount').value);

      if (!amount || amount <= 0) {
        alert('금액을 올바르게 입력해주세요.');
        return;
      }

      state.expenses.push({
        id: crypto.randomUUID(),
        amount
      });

      $('expenseAmount').value = '';
      render();
    }

    function removeMember(id) {
      state.members = state.members.filter(m => m.id !== id);
      render();
    }

    function removeExpense(id) {
      state.expenses = state.expenses.filter(e => e.id !== id);
      render();
    }

    function resetAll() {
      if (!confirm('참석자와 결제 내역을 전부 지울까요?')) return;
      state.members = [];
      state.expenses = [];
      state.receipts = [];
      $('receiptInput').value = '';
      $('drinkMemo').value = '';
      render();
    }

    function getSettlement() {
      const tables = getTables();
      const totalExpense = state.expenses.reduce((sum, e) => sum + e.amount, 0);
      const totalMembers = state.members.length;
      const perPersonGlobal = totalMembers ? Math.round(totalExpense / totalMembers) : 0;

      return tables.map(tableName => {
        const members = state.members.filter(m => m.table === tableName);
        const total = perPersonGlobal * members.length;

        return {
          tableName,
          members,
          total,
          perPerson: perPersonGlobal
        };
      });
    }

    function renderMembers() {
      const box = $('memberList');
      if (!state.members.length) {
        box.innerHTML = '<div class="empty">아직 참석자가 없습니다.</div>';
        return;
      }

      box.innerHTML = state.members.map(member => `
        <div class="item">
          <div class="item-top">
            <div>
              <div class="item-title">${escapeHtml(member.name)}</div>
            </div>
            <div class="row">
              <span class="badge">${escapeHtml(member.table)}</span>
              <button class="danger" onclick="removeMember('${member.id}')">삭제</button>
            </div>
          </div>
        </div>
      `).join('');
    }

    function renderExpenses() {
      const box = $('expenseList');
      if (!state.expenses.length) {
        box.innerHTML = '<div class="empty">아직 입력된 금액이 없습니다.</div>';
        return;
      }

      box.innerHTML = state.expenses.map((expense, index) => `
        <div class="item">
          <div class="item-top">
            <div>
              <div class="item-title">결제 ${index + 1}</div>
              <div class="muted">합산 대상 금액</div>
            </div>
            <div class="row">
              <span class="badge">${money(expense.amount)}</span>
              <button class="danger" onclick="removeExpense('${expense.id}')">삭제</button>
            </div>
          </div>
        </div>
      `).join('');
    }

    function renderSummary() {
      const totalMembers = state.members.length;
      const totalExpense = state.expenses.reduce((sum, e) => sum + e.amount, 0);
      const averageCost = totalMembers ? Math.round(totalExpense / totalMembers) : 0;

      $('totalMembers').textContent = `${totalMembers}명`;
      $('totalExpense').textContent = money(totalExpense);
      $('averageCost').textContent = money(averageCost);
    }

    function renderTables() {
      const list = $('tableList');
      const settlements = getSettlement();

      if (!settlements.length) {
        list.innerHTML = '<div class="empty">테이블 정보가 없어서 아직 정산할 수 없습니다.</div>';
        return;
      }

      list.innerHTML = settlements.map(item => `
        <div class="item">
          <div class="item-top">
            <div>
              <div class="item-title">${escapeHtml(item.tableName)}</div>
              <div class="muted">${item.members.map(m => escapeHtml(m.name)).join(', ') || '참석자 없음'}</div>
            </div>
            <span class="badge">${item.members.length}명</span>
          </div>
          <div class="summary-grid" style="margin-top: 12px;">
            <div class="summary-box">
              <div class="label">테이블 총액</div>
              <div class="value" style="font-size: 18px;">${money(item.total)}</div>
            </div>
            <div class="summary-box">
              <div class="label">1인당</div>
              <div class="value" style="font-size: 18px;">${money(item.perPerson)}</div>
            </div>
            <div class="summary-box">
              <div class="label">비고</div>
              <div class="muted">음료는 영수증 별도 확인</div>
            </div>
          </div>
        </div>
      `).join('');
    }

    function buildMessage(item) {
      const meetingDate = $('meetingDate').value;
      const formattedDate = meetingDate ? new Date(meetingDate).toLocaleDateString('ko-KR') : '날짜 미입력';
      const drinkMemo = $('drinkMemo').value.trim();

      return `[Big Talkers 정산 안내]\n` +
        `일시: ${formattedDate}\n` +
        `테이블: ${item.tableName}\n` +
        `참석자: ${item.members.map(m => m.name).join(', ')}\n` +
        `테이블 총액: ${money(item.total)}\n` +
        `1인당 금액: ${money(item.perPerson)}\n\n` +
        `음료는 영수증 확인 후 각자 따로 보내주시면 됩니다.` +
        (drinkMemo ? `\n음료 메모: ${drinkMemo}` : '');
    }

    function copyText(text) {
      navigator.clipboard.writeText(text)
        .then(() => alert('메시지를 복사했습니다.'))
        .catch(() => alert('복사에 실패했습니다. 직접 복사해주세요.'));
    }

    function renderMessages() {
      const list = $('messageList');
      const settlements = getSettlement();

      if (!settlements.length) {
        list.innerHTML = '<div class="empty">정산 결과가 생기면 테이블별 카톡 메시지를 만들 수 있습니다.</div>';
        return;
      }

      list.innerHTML = settlements.map((item, index) => {
        const text = buildMessage(item);
        return `
          <div class="item">
            <div class="item-top">
              <div class="item-title">${escapeHtml(item.tableName)} 메시지</div>
              <button class="success" onclick="copyText(window.__messages[${index}])">복사</button>
            </div>
            <textarea readonly>${text}</textarea>
          </div>
        `;
      }).join('');

      window.__messages = settlements.map(item => buildMessage(item));
    }

    function handleReceipts(event) {
      const files = [...event.target.files];
      state.receipts = files.map(file => ({
        id: crypto.randomUUID(),
        name: file.name,
        url: URL.createObjectURL(file)
      }));
      renderReceipts();
    }

    function renderReceipts() {
      const box = $('receiptPreview');
      if (!state.receipts.length) {
        box.innerHTML = '';
        return;
      }

      box.innerHTML = state.receipts.map(receipt => `
        <div class="preview-card">
          <img src="${receipt.url}" alt="${escapeHtml(receipt.name)}" />
          <div class="meta">${escapeHtml(receipt.name)}</div>
        </div>
      `).join('');
    }

    function render() {
      renderMembers();
      renderExpenses();
      renderSummary();
      renderTables();
      renderMessages();
      renderReceipts();
    }

    function loadSample() {
      state.members = [
        { id: crypto.randomUUID(), name: '진경', table: 'A테이블' },
        { id: crypto.randomUUID(), name: '민수', table: 'A테이블' },
        { id: crypto.randomUUID(), name: '서연', table: 'B테이블' },
        { id: crypto.randomUUID(), name: '현우', table: 'B테이블' },
        { id: crypto.randomUUID(), name: '지민', table: 'B테이블' }
      ];

      state.expenses = [
        { id: crypto.randomUUID(), amount: 120000 },
        { id: crypto.randomUUID(), amount: 18000 }
      ];

      $('meetingDate').value = new Date().toISOString().slice(0, 10);
      $('drinkMemo').value = '민수 - 아메리카노 / 서연 - 레몬에이드';
      render();
    }

    $('addMemberBtn').addEventListener('click', addMember);
    $('addExpenseBtn').addEventListener('click', addExpense);
    $('sampleBtn').addEventListener('click', loadSample);
    $('resetBtn').addEventListener('click', resetAll);
    $('receiptInput').addEventListener('change', handleReceipts);
    $('drinkMemo').addEventListener('input', renderMessages);

    render();

    window.removeMember = removeMember;
    window.removeExpense = removeExpense;
    window.copyText = copyText;
  </script>
</body>
</html>
